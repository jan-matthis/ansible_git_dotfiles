# Git dotfiles

Ansible role to install and update dotfiles using a bare Git repository.

Automatises the technique described in [The best way to store your dotfiles: A bare Git repository](https://www.atlassian.com/git/tutorials/dotfiles):

> The technique consists in storing a Git bare repository in a "side" folder (like $HOME/.cfg or $HOME/.myconfig) using a specially crafted alias so that commands are run against that repository and not the usual .git local folder, which would interfere with any other Git repositories around.


## Installation

```commandline
$ ansible-galaxy install jan_matthis.git_dotfiles
```

## Variables

```yaml
# Dotfiles repository
git_dotfiles_repo: "https://github.com/jan-matthis/dotfiles.git"

# Alias to manage dotfiles
git_dotfiles_alias: "cfg"

# Directory for dotfiles
git_dotfiles_dir: "{{ ansible_env.HOME }}"

# Directory for .git/ of dotfiles repository
git_dotfiles_dir_dot_git: "{{ ansible_env.HOME }}/.cfg/"

# Directory for backup files
git_dotfiles_dir_backup: "{{ ansible_env.HOME }}/.config-backup"

# File in which alias gets defined, empty string to not set it
git_dotfiles_alias_file: "{{ ansible_env.HOME }}/.aliases"
```


## Example

```yaml
- hosts: servers
  include_role:
    name: jan_matthis.git_dotfiles
  vars:
    git_dotfiles_url: "https://github.com/jan-matthis/dotfiles.git"
```


## Testing

Tests can be run using [`molecule`](https://molecule.readthedocs.io/en/latest/) and `docker`.


## License

MIT
