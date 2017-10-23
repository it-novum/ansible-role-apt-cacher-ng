# Ansible Role - Configures apt-cacher-ng

## Variables

### Required

 - acng_server: Set this to the inventory name of your acng master server

### Defaults

 - acng_apt_components_ubuntu: apt repo components that should be loaded (default: "main restricted universe multiverse")
 - acng_apt_components_debian: apt repo components that should be loaded (default: "main contrib non-free")
 - acng_apt_source: if deb-src should be included (default: no)
 - acng_proxy: set the proxy that apt-cacher-ng should use, empty string means no proxy (default: "")
 - acng_backends: a list of additional backends for apt-cacher-ng (default: [])
 
 
 ## acng_backends

You can configure some special repos with this, for example openitcockpit:

```yaml
- hosts: all
  roles: acng
  vars:
    acng_server: mymaster
    acng_backends:
      - name: openitcockpit
        url: "https://secret:PUTLICENSEHERE@packages.openitcockpit.com/repositories/"
        base: "packages.openitcockpit.com/repositories"
```

Then
```
deb http://127.0.0.1/packages.openitcockpit.com/repositories/xenial xenial main
```
in sources.list will work.
