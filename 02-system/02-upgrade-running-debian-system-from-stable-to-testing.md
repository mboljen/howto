# Howto

## System administration

### Upgrade a running Debian system from stable to testing

Make a backup of the current settings to avoid getting lost in a wrongly configured system. Note that upgrading to `testing` is not reversible, this means once upgraded it is impossible to downgrade to `stable` again.

```console
$ cp /etc/apt/sources.list{,.bak}
```

Now apply the following changes to the configuration file `/etc/apt/sources.list` in order to switch from `stable` to `testing`.

```console
$ sed -i -e 's/ \(stable|buster\)/ testing/ig' /etc/apt/sources.list
```

Update the package lists and download the new packages.

```console
$ apt-get update
$ apt-get --download-only dist-upgrade
```

Finally, install all downloaded packages and update the distribution to `testing`.

```console
$ apt-get dist-upgrade
```

---
[Return to Index](../README.md)
