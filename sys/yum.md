# Yum

## Commands
```sh
# Show version of a package in the repository
yum list --showduplicates package

# Show the list but with the FULL NAMES to use for specific version install
yum search package --show-duplicates

# List of outdated packages
yum list updates

# List of installed packages
yum list installed

# Show version and other info of a package
yum info splunkforwarder

# Downgrade a package
sudo yum downgrade vim-common.x86_64-2:7.4.629-8.el7_9
```

## Yum versionlock plugin

### How it works:
The configuration will not allow to change the version of the package that was installed at the time the locking was performed or at the specified version.
Yum will attempt to update all packages, while excluding the packages listed in the versionlock file.

Installation of the plugin creates `/etc/yum/pluginconf.d/versionlock.list` on the system, it contains a list of packages that should not be upgraded.

### Useful links
- https://support.datastax.com/s/article/How-to-lock-a-specific-package-version-using-yum

### Commands
```sh
# Show version of a package in the repository
yum list --showduplicates yum-plugin-versionlock

# Install a the plugin
yum install yum-plugin-versionlock -y

# To display the list
yum versionlock list

# To discard the list
sudo yum versionlock clear

# Lock a package version...
sudo yum versionlock nameofthepackage-5.2.5 # idempotent command
# ...OR edit the file directly
sudo vim /etc/yum/pluginconf.d/versionlock.list

```