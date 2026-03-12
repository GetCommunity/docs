# 1Password

[1Password](https://1password.com/) is a password manager that helps you store and manage your passwords securely. It offers features such as password generation, secure storage, and easy access across devices.

## 1Password for Developers

1Password provides a command-line tool called `op` that allows developers to access their 1Password vaults and retrieve secrets directly from the terminal. This can be particularly useful for managing environment variables and secrets in development workflows.

### Installing the 1Password CLI

To install the 1Password CLI, you can follow the instructions provided in the [official documentation](https://developer.1password.com/docs/cli/get-started#install).

### Using the 1Password CLI

Once you have the `op` CLI installed, you can use it to retrieve secrets from your 1Password vault. For example, you can use the following command to inject secrets into your environment:

```bash
# Create .env files from templates
op inject -i .env.template.dev -o .dev.vars
op inject -i .env.template.dev -o .env
op inject -i .env.template.prod -o .env.prod

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
