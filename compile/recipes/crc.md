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

[machine]
    name="crcbuild"
    from="golang"

[devenv]
    name="crcbuild"
    from="gofedora"
```

### machine-compile
```sh interactive
machine ${MACHINE_NAME} from ${MACHINE_FROM}
machine ${MACHINE_NAME} playbook ${COMPILE_PLAYBOOK}
machine ${MACHINE_NAME} exec tar cf - ${COMPILE_OUT_PATH} | tar xf - -C ~
```

### devenv-compile
```sh interactive
devenv ${DEVENV_NAME} from ${DEVENV_FROM}
devenv ${DEVENV_NAME} playbook ${COMPILE_PLAYBOOK} -e target_user="gbraad"
```

