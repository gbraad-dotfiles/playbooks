Compile CRC
===========


This playbook compiles the CRC (OpenShift Local) binary from source. It is designed to run on a remote host, typically a Linux machine.

It depends on:

  - Galaxy: `gbraad.dotfiles`
  - Galaxy: `gbraad.dotfiles-devenv`

It will checkout the `crc` repository, compile the binary inside a IDE container, and the resultingh binary will be available on the host in the 
projects' `out` directory.



## Usage

```zsh
$ ansible-galaxy install gbraad.dotfiles gbraad.dotfiles-devenv
$ ansible-playbook -i 100.64.142.12, site.yml -u runner
```
