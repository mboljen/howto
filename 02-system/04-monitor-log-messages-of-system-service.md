# Howto

## System administration

### Monitor log messages of system service

Use the following command to continuously monitor the log messages of a system service

```console
$ sudo journalctl -f -u name-of-service
```

In this example, the output of the service `autosuspend.service` will be monitored:

```console
$ sudo journalctl -f -u autosuspend
```

---
[Return to Index](../README.md)
