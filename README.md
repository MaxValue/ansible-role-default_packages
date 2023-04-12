# Ansible Role: Default Packages

An Ansible Role that installs a set of predefined packages on the host.

[TOC]

## Requirements

_None._

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### Main Variables

    packages:
      - zsh
      - mosh
      - rsync
      - vim

The optional variable `packages` defines the list of packages to be installed.
Each item can also be a mapping; in this case, there should be a key `all` which is the fallback name
for all package managers. Using the package manager name as key
you can define an alternative package name for that specific package manager.
Using `''` as a value for a package manager skips this package for that package manager.

### Internal variables

These are variables internally created by the role. Please do not use them in your code.

    _packages_selected_raw

The internal variable `_packages_selected_raw` contains a string of comma separated package names taken from the `packages` variable.

    _packages_selected

The internal variable `_packages_selected` contains a list of package names taken from the `_packages_selected_raw` variable.

## Dependencies

* The community.general collection: `ansible-galaxy collection install --force community.general`

## Example Playbooks

### Normal usage

    ---
    # This installs the built-in list of packages
    - hosts: localhost
      roles:
        - role:
            name: maxvalue.default_packages
    ...

### Provide a specific list

    ---
    # This installs the given list of packages
    - hosts: localhost
      roles:
        - role:
            name: maxvalue.default_packages
          vars:
            packages:
              - all: false
                homebrew: little-snitch
    ...

## License

[MIT](LICENSE.txt)

## Sponsors

You can support the development of this role and other similar roles by donating to one of the accounts below.

* [bymeacoffee](https://www.buymeacoffee.com/publicbetamax)
* [liberapay](https://de.liberapay.com/maxvalue/)
* [ko-fi](https://ko-fi.com/publicbetamax)
* [Patreon](patreon.com/publicbetamax)

## Author Information

This role was created in 2023 by Max Fuxjäger:
* Mastodon: @maxvalue@chaos.social
* Matrix: @ypsilon:matrix.org
