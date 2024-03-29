Provisioning and configuring the hub
------------------------------------

For development and testing we provision a PINE64 board using an ubuntu base image that we then customize using ansible.

To download the base image use `make download-base`.

Then write the image to an SD card using your tool of choice (https://etcher.io/ seems like a fluffy choice for OSX) and boot the board, making sure you have a working DHCP setup.

For example, you can use OSX's 'Internet Sharing' feature to i.e. share the wifi connection over ethernet and connect the board directly via ethernet.
This has the added advantage that the board has no direct access to the rest of your network (and vice versa). In this case the board will receive an IP address of `192.168.2.1`` by default, which is also te default value configured in `etc/ploy.conf`.

The first step is to bootstrap the booted board into a state where we can configure it via ansible.
This is done using a helper tool called `ploy` which is a modular configuration system that (in this case) combines `ansible <http://docs.ansible.com/ansible/>`_ and `fabric <http://www.fabfile.org/>`_.
The `Makefile` installs a local instance of `ploy` and its dependencies by default, so you should run `make` first.

Then you can run `make bootstrap` and watch the show... After a minute or two, the board should reboot and is now ready for action.
