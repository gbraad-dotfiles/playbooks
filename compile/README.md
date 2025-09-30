Compilation
===========


This playbook compiles from source defined in a playbook. It is designed to run on a remote host, typically a Linux machine.

It will checkout the repository, compile the binary inside a build container, and the resulting binary will be available on the host in the 
projects' `out` directory.


## Usage

### `devenv playbook` builds inside a container
```sh evaluate
devenv gofedora playbook recipes/crc.yml
```

### `machine playbook` builds inside a virtual machine
```sh evaluate
machine gofedora playbook recipes/crc.yml
```

### `runner playbook` builds locally
```sh evaluate
ansible-playbook recipes/crc.yml
```


## Run the playbook on a runner

Use either to ensure you have the required Ansible Galaxy roles installed

### Install `dependencies` using rolenames

```sh evaluate
ansible-galaxy install gbraad.dotfiles gbraad.dotfiles-devenv gbraad.dotfiles-machine
```

### Install `requirements` to run all roles
```sh evaluate
ansible-galaxy install -r requirements.yml
```


### `playbook devenv` targets an IP and builds using a container

```sh evaluate
ansible-playbook -i 100.64.142.12, compile-using-devenv.yml -u runner -e playbook_name="recipes/crc.yml"
```

### `playbook machine` targets an IP and builds using a virtual machine

```sh evaluate
ansible-playbook -i 100.64.142.12, compile-using-machine.yml -u runner -e playbook_name="recipes/crc.yml"
```

### `playbook runner` targets the local machine as user to build

```sh evaluate
ansible-playbook recipes/crc.yml -e target_user="runner"
```


## Alternative options

Using [remote_playbook](https://github.com/gbraad-dotfiles/upstream/blob/65c4cbf98b7193d87936415beb5c5bd05e51476d/zsh/.zshrc.d/ansible.zsh#L2)

### Using the `remote_playbook` command shows
```sh evaluate
remote_playbook podman test recipes/crc.yml
remote_playbook macadam test recipes/crc.yml
remote_playbook user@test recipes/crc.yml
```
