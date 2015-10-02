# 'python-gmusicapi' Debian package

This is the source for the Tizonia project's Debian package of the
[MechanicalSoup](https://github.com/hickford/MechanicalSoup) Python library. It is in
no way specific to Tizonia and may also be used by other applications to gain
access to the Google Play Music streaming services.

The goal is to allow installation of Simon Weber's
[gmusicapi](https://github.com/simon-weber/gmusicapi) library, including all
its dependencies, using Debian's apt-get instead of 'pip'.

## Building the Debian package

1. Download the 'MechanicalSoup' git repo and install all the necessary Debian
   development packages. To do this, just run the supplied bootstrap script
   with a valid 'MechanicalSoup' git tag. E.g.:
   ```bash

        $ ./bootstrap.sh v0.3.1

   ```

2. Now run the usual autotools sequence to configure, build, install and
   uninstall the 'python-mechanicalsoup' Debian package.
   ```bash

        $ ./configure
        $ make
        $ make install
        $ make uninstall

   ```
