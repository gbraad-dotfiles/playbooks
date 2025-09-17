# Compile CRC


### info

This is an Actionfile that describes the build process of CRC using an Ansible playbook as recipe.

```
run crc.md compile devenv
run crc.md compile machine
```


### config
```ini
[compile]
    playbook="crc.yml"
    out_path="Projects/crc-org/crc/out"
    out_dest="${HOME}"
    flatten=0

[machine]
    name="crcbuild"
    from="golang"

[devenv]
    name="crcbuild"
    from="gofedora"
```

### Compile using playbook on `machine`
```sh evaluate
machine ${MACHINE_NAME} from ${MACHINE_FROM}
machine ${MACHINE_NAME} playbook ${COMPILE_PLAYBOOK}
sudo rm -rf ${COMPILE_OUT_DEST}/${COMPILE_OUT_PATH}
machine ${MACHINE_NAME} exec tar cf - ${COMPILE_OUT_PATH} | tar xf - -C ${COMPILE_OUT_DEST} --strip-components=${COMPILE_FLATTEN}
```

### Compile using playbook on `devenv`
```sh evaluate
devenv ${DEVENV_NAME} from ${DEVENV_FROM}
devenv ${DEVENV_NAME} playbook ${COMPILE_PLAYBOOK} -e target_user="gbraad"
```

