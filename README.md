ansible role for aehostd
========================

This ansible role installs and configures
[aehostd](https://www.ae-dir.com/aehostd.html)
as NSS/PAM service on Linux systems.

The installation differs a bit for the supported platforms:

  * Debian buster
  * CentOS 7.7 and 8
  * openSUSE Leap 15.1+ and Tumbleweed
  * SLE 15SP1 or newer

openSUSE / SLE
--------------

Native packages are built in OBS repo
[home:stroeder:iam](https://build.opensuse.org/project/show/home:stroeder:iam)
for the various openSUSE and SLE versions.

The appropriate download repo has to be added before like this:

   zypper addrepo -f https://download.opensuse.org/repositories/home:/stroeder:/iam/openSUSE_Tumbleweed/

See also: [List of zypper repos](https://download.opensuse.org/repositories/home:/stroeder:/iam/)


Debian
------

A Python virtual environment is used to install _aehostd_.

Thus build tools are temporarily installed for compiling the C
wrapper module [ldap0](https://pypi.org/project/ldap0/).

For mass installation you should setup at least a minimal
HTTP server hosting pre-compiled wheels and set the ansible
variable _aehostd_pip_index_url_ accordingly.
