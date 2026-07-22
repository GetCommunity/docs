# 1Password

[1Password](https://1password.com/) is a password manager that helps you store and manage your passwords securely. It offers features such as password generation, secure storage, and easy access across devices.

## 1Password for Developers

1Password provides a command-line tool called `op` that allows developers to access their 1Password vaults and retrieve secrets directly from the terminal. This can be particularly useful for managing environment variables and secrets in development workflows.

### Installing the 1Password CLI

To install the 1Password CLI, you can follow the instructions provided in the [official documentation](https://developer.1password.com/docs/cli/get-started#install).

### Installing 1Password CLI on a Server

To install the 1Password CLI on a Linux amd64 server, you can use the following command:

```bash
ARCH="amd64"; \
    OP_VERSION="v$(curl https://app-updates.agilebits.com/check/1/0/CLI2/en/2.0.0/N -s | grep -Eo '[0-9]+\.[0-9]+\.[0-9]+')"; \
    curl -sSfo op.zip \
    https://cache.agilebits.com/dist/1P/op2/pkg/"$OP_VERSION"/op_linux_"$ARCH"_"$OP_VERSION".zip \
    && unzip -od /usr/local/bin/ op.zip \
    && rm op.zip
```

### Installing 1Password CLI in a Docker Container

```Dockerfile
COPY --from=1password/op:2 /usr/local/bin/op /usr/local/bin/op
```

### Using the 1Password CLI

Once you have the `op` CLI installed, you can use it to retrieve secrets from your 1Password vault. For example, you can use the following command to inject secrets into your environment:

### Logging Into 1Password

```bash
# Add Account
op account add
# Enter account URL, email, secret key, and account password
# > getcommunityinc.1password.com

# Sign In
eval $(op signin)
```

### Loading Secrents from Env Templates

```bash
# Create .env files from templates
op inject -i .env.template.dev -o .dev.vars
op inject -i .env.template.dev -o .env
op inject -i .env.template.prod -o .env.prod
op inject -i .env.template.test -o .env.test

# Start development server with environment variables
op run --env-file=.env.template.dev -- pnpm dev

# Build production with environment variables
op run --env-file=.env.template.prod -- pnpm build
```

### Loading Secrets into the Shell

You can also create a shell function to load secrets from 1Password into your current shell session.

We recommend adding the following function to your shell configuration file (e.g., `.bashrc`, `.zshrc`, `.profile`, etc.):

```bash
loadop() {
    eval "$(
        op inject -i "$1" | sed 's/^/export /'
    )" > /dev/null
}
```

Then you can use the `loadop` function to load secrets from a specified file:

```bash
loadop .env.template
loadop .env.template.test
loadop .env.template.dev
loadop .env.template.prod
```
