# Debian/Ubuntu packages caching service

## Requirements
* VirtualBox/Parallels
* Vagrant

## Deployment
```
$ vagrant up
```

## Ports
* 3142: apt-cacher

## Configuration
* enable HTTPS traffic to private Launchpad repositories
```
echo "PassThroughPattern: private-ppa\.launchpad\.net:443$" | sudo tee -a /etc/apt-cacher-ng/acng.conf
```
