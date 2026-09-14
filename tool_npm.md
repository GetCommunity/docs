# NPM

## Versioning

### Patch Release = 0.0.0 → 0.0.1

```bash
npm version patch
```

### Minor Release = 0.0.0 → 0.1.0

```bash
npm version minor
```

### Major Release = 0.0.0 → 1.0.0

```bash
npm version major
```

### Explicit Release

```bash
npm version 1.2.3
```

### Custom git commit message

```bash
npm version patch -m "Release v%s"
```

## Prerelease Version Shifting

### Major Shift = 1.0.0 → 2.0.0-alpha.0

```bash
npm version premajor --preid=alpha
```

### Minor Shift = 1.0.0 → 1.1.0-beta.0

```bash
npm version preminor --preid=beta
```

### Patch Shift = 1.0.0 → 1.0.1-rc.0

```bash
npm version prepatch --preid=rc
```

### Next Shift = 1.0.0 → 1.0.1-next.0

```bash
# make the first prerelease
npm version prerelease --preid=next
npm publish --tag=next

# on subsequent prereleases
npm version prerelease
npm publish --tag=next
```
