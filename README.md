# Minimal Mesos

A Vagrant VM for quickly setting up a minimal mesos local setup.

### Versions used
Vagrant 2.0.2
VirtualBox 5.2
Mesos 1.5.0
Marathon 1.6
ZooKeeper 3.4.5

### Start it

```sh
vagrant up --provider virtualbox
```

### Access it

Mesos:
```sh
http://192.168.33.10:5050/
```

Marathon:
```sh
http://192.168.33.10:8080/
```
