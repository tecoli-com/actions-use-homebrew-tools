# actions-use-homebrew-tools

![actions-use-homebrew-tools](https://github.com/tecoli-com/actions-use-homebrew-tools/actions/workflows/test.yml/badge.svg)

This GitHub action isntall homebrew packages and cache them for later
use.  When executed next time with same package list, and any other
environment are not changed, installed files are extracted from the
cached archive.

When valid cached archive is not found, all packages are installed by
`brew` command.  Incremental installation is not supported.

This actions assumes `brew` command is already installed.  So please
install it before calling if not available.

Installed files are taken by comparing directory before and after
installation.  So it takes time to find them if many files are already
installed before command execution.

Output is same as
[`@actions/cache`](https://github.com/actions/cache).

## Usage

```yaml
# inputs:
#   tools: { required: true,  type: string }
#   cache: { required: false, type: string, default: yes }
#   key:   { required: false, type: string }

- uses: tecoli-com/actions-use-homebrew-tools@v0
  with:

    # homebrew packages
    tools: ''

    # Cache strategy
    #
    # yes:      activate cache
    # no:       no cache
    # workflow: effective within same workflow (mainly for test)
    #
    cache: yes

    # Additional cache key
    key: ''
```

## Example

```yaml
- uses: tecoli-com/actions-use-homebrew-tools@v0
  with:
    tools: rcs
```

## See Also

### [tecoli-com/actions](https://github.com/tecoli-com/actions)

### [`@tecoli-com/actions-install-and-cache`](https://github.com/tecoli-com/actions-install-and-cache)

This action is just a glue for
[`@actions-install-and-cache`](https://github.com/tecoli-com/actions-install-and-cache).
