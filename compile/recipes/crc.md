# Compile CRC


### info

This is an Actionfile that describes the build process of CRC using an Ansible playbook as recipe.

```sh
run crc.md compile devenv
run crc.md compile machine
```


### config
```ini
[compile]
    playbook="crc.yml"
    out_path="Projects/crc-org/crc/out"
```

### machine-compile
```sh interactive
machine crcbuild from golang
machine crcbuild playbook ${COMPILE_PLAYBOOK}
machine crcbuild exec tar cf - ${COMPILE_OUT_PATH} | tar xf - -C ~
```

### devenv-compile
```sh interactive
devenv crcbuild from gofedora
devenv crcbuild playbook ${COMPILE_PLAYBOOK} -e target_user="gbraad"
```

