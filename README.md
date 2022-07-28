ansible role for aehostd
========================

This ansible role installs and configures
[aehostd](https://www.ae-dir.com/aehostd.html)
as NSS/PAM service on Linux systems.

This ansible role manages the following system-wide configuration files
which might conflict with other configuration requirements in your
environment:

  * /etc/nscd.conf
  * /etc/nsswitch.conf
  * /etc/pam.d/common*
  * /etc/ssh/sshd_config
  * /etc/sudoers

Thus you should fork this ansible role and maintain your own site-specific
deployment.

The installation differs a bit for the supported platforms:

  * Debian buster or newer
  * Ubuntu focal or newer
  * RHEL-alike systems 8+ (Red-Hat Enterprise Linux, AlmaLinux, Rocky Linux, CentOS)
  * openSUSE Leap 15.4+ and Tumbleweed
  * SLE 15SP4 or newer

openSUSE / SLE
--------------

Native RPM packages used by this role are built in OBS repo
_home:stroeder:iam_ for various openSUSE and SLE versions.

You can set ansible variable _aehostd_pkg_repos_ in your group vars
to install packages from your local mirror.

See also:
  * [List of zypper repos](https://download.opensuse.org/repositories/home:/stroeder:/iam/)
  * [OBS package home:stroeder:iam/aehostd](https://build.opensuse.org/package/show/home:stroeder:iam/aehostd)
  * [OBS package home:stroeder:iam/aehostd-modules](https://build.opensuse.org/package/show/home:stroeder:iam/aehostd-modules)

Debian/Ubuntu
-------------

Native Debian/Ubuntu packages used by this role are available
in a custom APT repository.

You can set ansible variable _aehostd_pkg_repos_ in your group vars
to install packages from your local mirror.

See also:
  * [APT repos for Debian](https://ae-dir.com/repo/debian/)
  * [APT repos for Ubuntu](https://ae-dir.com/repo/ubuntu/)

RHEL-alike
----------

A Python virtual environment is used to install _aehostd_.

Thus build tools are temporarily installed for compiling the C
wrapper module [ldap0](https://pypi.org/project/ldap0/).

For mass installation you should setup at least a minimal
HTTP server hosting pre-compiled wheels and set the ansible
variable _aehostd_pip_index_url_ accordingly.
