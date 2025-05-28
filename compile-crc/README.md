Compile CRC
===========


This playbook compiles the CRC (OpenShift Local) binary from source. It is designed to run on a remote host, typically a Linux machine.

It depends on:

  - Galaxy: `gbraad.dotfiles`
  - Galaxy: `gbraad.dotfiles-devenv`

It will checkout the `crc` repository, compile the binary inside a IDE container, and the resultingh binary will be available on the host in the 
projects' `out` directory.



## Usage

### Install dependencies

Ensure you have the required Ansible Galaxy roles installed:
```zsh
$ ansible-galaxy install gbraad.dotfiles gbraad.dotfiles-devenv
```

```zsh
$ ansible-galaxy install -r requirements.yml
```


### Run the playbook
```zsh
$ ansible-playbook -i 100.64.142.12, compile-crc-[devenv].yml -u runner
```
