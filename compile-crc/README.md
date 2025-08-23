Compile CRC
===========


This playbook compiles the CRC (OpenShift Local) binary from source. It is designed to run on a remote host, typically a Linux machine.

It will checkout the `crc` repository, compile the binary inside a IDE container, and the resultingh binary will be available on the host in the 
projects' `out` directory.


## Usage

### Run the playbook in devenv
```zsh
$ devenv gofedora playbook compile.yml
```


### Run the playbook in machine
```zsh
$ machine gofedora playbook compile.yml
```


### Using [remote_playbook](https://github.com/gbraad-dotfiles/upstream/blob/65c4cbf98b7193d87936415beb5c5bd05e51476d/zsh/.zshrc.d/ansible.zsh#L2)
```zsh
$ remote_playbook podman test ~/playbook.yml
$ remote_playbook macadam test ~/playbook.yml
$ remote_playbook user@test ~/playbook.yml
```


### Run the playbook on a runner using devenv

Ensure you have the required Ansible Galaxy roles installed:
```zsh
$ ansible-galaxy install gbraad.dotfiles gbraad.dotfiles-devenv
```
or 

```zsh
$ ansible-galaxy install -r requirements.yml
```

```zsh
$ ansible-playbook -i 100.64.142.12, in-runner.yml -u runner
```
