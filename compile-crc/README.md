Compile CRC
===========


This playbook compiles the CRC (OpenShift Local) binary from source. It is designed to run on a remote host, typically a Linux machine.

It will checkout the `crc` repository, compile the binary inside a IDE container, and the resultingh binary will be available on the host in the 
projects' `out` directory.


## Usage

### devenv-command used for build
```sh interactive
devenv gofedora playbook compile.yml
```


### machine-command used for build
```sh interactive
machine gofedora playbook compile.yml
```


## Run the playbook on a runner

Use either to ensure you have the required Ansible Galaxy roles installed

### dependencies using rolenames

```sh interactive
ansible-galaxy install gbraad.dotfiles gbraad.dotfiles-devenv gbraad.dotfiles-machine
```

### requirements file to install all roles
```sh interactive
ansible-galaxy install -r requirements.yml
```


### devenv-playbook targeting an IP

```sh interactive
ansible-playbook -i 100.64.142.12, compile-using-devenv.yml -u runner
```

### machine-playbook targeting an IP

```sh interactive
ansible-playbook -i 100.64.142.12, compile-using-machine.yml -u runner
```

### runner-playbook targeting the `runner` as user

```sh interactive
ansible-playbook compile.yml -e '{"target_user": "runner"}'
```


## Alternative options

Using [remote_playbook](https://github.com/gbraad-dotfiles/upstream/blob/65c4cbf98b7193d87936415beb5c5bd05e51476d/zsh/.zshrc.d/ansible.zsh#L2)

### remote_playbook
```sh interactive
remote_playbook podman test ~/playbook.yml
remote_playbook macadam test ~/playbook.yml
remote_playbook user@test ~/playbook.yml
```
