==========
Change log
==========
All notable changes to this project will be documented in this file. The format
is based on `Keep a Changelog`_ and this project
adheres to `Semantic Versioning`_.

.. _`Keep a Changelog`: http://keepachangelog.com/
.. _`Semantic Versioning`: http://semver.org/


1.0.5 - 2020-12-29
------------------

Added
~~~~~
* IPv6 support in nft method.
* Intercept DNS requests sent by systemd-resolved.
* Set default tmark.
* Fix python2 server compatibility.
* Python 3.9 support.

Fixed
~~~~~
* Change license text to LGPL-2.1
* Fix #494 sshuttle caught in infinite select() loop.
* Include sshuttle version in verbose output.
* Add psutil as dependency in setup.py
* When subnets and excludes are specified with hostnames, use all IPs.
* Update/document client's handling of IPv4 and IPv6.
* Update sdnotify.py documentation.
* Allow no remote to work.
* Make prefixes in verbose output more consistent.
* Make nat and nft rules consistent; improve rule ordering.
* Make server and client handle resolv.conf differently.
* Fix handling OSError in FirewallClient#__init__
* Refactor automatic method selection.

Removed
~~~~~~~
* Drop testing of Python 3.5


1.0.4 - 2020-08-24
------------------

Fixed
~~~~~
* Allow Mux() flush/fill to work with python < 3.5
* Fix parse_hostport to always return string for host.
* Require -r/--remote parameter.
* Add missing package in OpenWRT documentation.
* Fix doc about --listen option.
* README: add Ubuntu.
* Increase IP4 ttl to 63 hops instead of 42.
* Fix formatting in installation.rst


1.0.3 - 2020-07-12
------------------

Fixed
~~~~~
* Ask setuptools to require Python 3.5 and above.
* Add missing import.
* Fix formatting typos in usage docs


1.0.2 - 2020-06-18
------------------

Fixed
~~~~~
* Leave use of default port to ssh command.
* Remove unwanted references to Python 2.7 in docs.
* Replace usage of deprecated imp.
* Fix connection with @ sign in username.


1.0.1 - 2020-06-05
------------------

Fixed
~~~~~
* Errors in python long_documentation.


1.0.0 - 2020-06-05
------------------

Added
~~~~~
* Python 3.8 support.
* sshpass support.
* Auto sudoers file (#269).
* option for latency control buffer size.
* Docs: FreeBSD'.
* Docs: Nix'.
* Docs: openwrt'.
* Docs: install instructions for Fedora'.
* Docs: install instructions for Arch Linux'.
* Docs: 'My VPN broke and need a solution fast'.

Removed
~~~~~~~
* Python 2.6 support.
* Python 2.7 support.

Fixed
~~~~~
* Remove debug message for getpeername failure.
* Fix crash triggered by port scans closing socket.
* Added "Running as a service" to docs.
* Systemd integration.
* Trap UnicodeError to handle cases where hostnames returned by DNS are invalid.
* Formatting error in CHANGES.rst
* Various errors in documentation.
* Nftables based method.
* Make hostwatch locale-independent (#379).
* Add tproxy udp port mark filter that was missed in #144, fixes #367.
* Capturing of local DNS servers.
* Crashing on ECONNABORTED.
* Size of pf_rule, which grew in OpenBSD 6.4.
* Use prompt for sudo, not needed for doas.
* Arch linux installation instructions.
* tests for existing PR-312 (#337).
* Hyphen in hostname.
* Assembler import (#319).


0.78.5 - 2019-01-28
-------------------

Added
~~~~~
* doas support as replacement for sudo on OpenBSD.
* Added ChromeOS section to documentation (#262)
* Add --no-sudo-pythonpath option

Fixed
~~~~~
* Fix forwarding to a single port.
* Various updates to documentation.
* Don't crash if we can't look up peername
* Fix missing string formatting argument
* Moved sshuttle/tests into tests.
* Updated bandit config.
* Replace path /dev/null by os.devnull.
* Added coverage report to tests.
* Fixes support for OpenBSD (6.1+) (#282).
* Close stdin, stdout, and stderr when using syslog or forking to daemon (#283).
* Changes pf exclusion rules precedence.
* Fix deadlock with iptables with large ruleset.
* docs: document --ns-hosts --to-ns and update --dns.
* Use subprocess.check_output instead of run.
* Fix potential deadlock condition in nft_get_handle.
* auto-nets: retrieve routes only if using auto-nets.


0.78.4 - 2018-04-02
-------------------

Added
~~~~~
* Add homebrew instructions.
* Route traffic by linux user.
* Add nat-like method using nftables instead of iptables.

Changed
~~~~~~~
* Talk to custom DNS server on pod, instead of the ones in /etc/resolv.conf.
* Add new option for overriding destination DNS server.
* Changed subnet parsing. Previously 10/8 become 10.0.0.0/8.  Now it gets
  parsed as 0.0.0.10/8.
* Make hostwatch find both fqdn and hostname.
* Use versions of python3 greater than 3.5 when available (e.g. 3.6).

Removed
~~~~~~~
* Remove Python 2.6 from automatic tests.

Fixed
~~~~~
* Fix case where there is no --dns.
* [pf] Avoid port forwarding from loopback address.
* Use getaddrinfo to obtain a correct sockaddr.
* Skip empty lines on incoming routes data.
* Just skip empty lines of routes data instead of stopping processing.
* [pf] Load pf kernel module when enabling pf.
* [pf] Test double restore (ipv4, ipv6) disables only once; test kldload.
* Fixes UDP and DNS proxies binding to the same socket address.
* Mock socket bind to avoid depending on local IPs being available in test box.
* Fix no value passed for argument auto_hosts in hw_main call.
* Fixed incorrect license information in setup.py.
* Preserve peer and port properly.
* Make --to-dns and --ns-host work well together.
* Remove test that fails under OSX.
* Specify pip requirements for tests.
* Use flake8 to find Python syntax errors or undefined names.
* Fix compatibility with the sudoers file.
* Stop using SO_REUSEADDR on sockets.
* Declare 'verbosity' as global variable to placate linters.
* Adds 'cd sshuttle' after 'git' to README and docs.
* Documentation for loading options from configuration file.
* Load options from a file.
* Fix firewall.py.
* Move sdnotify after setting up firewall rules.
* Fix tests on Macos.


0.78.3 - 2017-07-09
-------------------
The "I should have done a git pull" first release.

Fixed
~~~~~
* Order first by port range and only then by swidth


0.78.2 - 2017-07-09
-------------------

Added
~~~~~
* Adds support for tunneling specific port ranges (#144).
* Add support for iproute2.
* Allow remote hosts with colons in the username.
* Re-introduce ipfw support for sshuttle on FreeBSD with support for --DNS option as well.
* Add support for PfSense.
* Tests and documentation for systemd integration.
* Allow subnets to be given only by file (-s).

Fixed
~~~~~
* Work around non tabular headers in BSD netstat.
* Fix UDP and DNS support on Python 2.7 with tproxy method.
* Fixed tests after adding support for iproute2.
* Small refactoring of netstat/iproute parsing.
* Set started_by_sshuttle False after disabling pf.
* Fix punctuation and explain Type=notify.
* Move pytest-runner to tests_require.
* Fix warning: closed channel got=STOP_SENDING.
* Support sdnotify for better systemd integration.
* Fix #117 to allow for no subnets via file (-s).
* Fix argument splitting for multi-word arguments.
* requirements.rst: Fix mistakes.
* Fix typo, space not required here.
* Update installation instructions.
* Support using run from different directory.
* Ensure we update sshuttle/version.py in run.
* Don't print python version in run.
* Add CWD to PYTHONPATH in run.


0.78.1 - 2016-08-06
-------------------
* Fix readthedocs versioning.
* Don't crash on ENETUNREACH.
* Various bug fixes.
* Improvements to BSD and OSX support.


0.78.0 - 2016-04-08
-------------------

* Don't force IPv6 if IPv6 nameservers supplied. Fixes #74.
* Call /bin/sh as users shell may not be POSIX compliant. Fixes #77.
* Use argparse for command line processing. Fixes #75.
* Remove useless --server option.
* Support multiple -s (subnet) options. Fixes #86.
* Make server parts work with old versions of Python. Fixes #81.


0.77.2 - 2016-03-07
-------------------

* Accidentally switched LGPL2 license with GPL2 license in 0.77.1 - now fixed.


0.77.1 - 2016-03-07
-------------------

* Use semantic versioning. http://semver.org/
* Update GPL 2 license text.
* New release to fix PyPI.


0.77 - 2016-03-03
-----------------

* Various bug fixes.
* Fix Documentation.
* Add fix for MacOS X issue.
* Add support for OpenBSD.


0.76 - 2016-01-17
-----------------

* Add option to disable IPv6 support.
* Update documentation.
* Move documentation, including man page, to Sphinx.
* Use setuptools-scm for automatic versioning.


0.75 - 2016-01-12
-----------------

* Revert change that broke sshuttle entry point.


0.74 - 2016-01-10
-----------------

* Add CHANGES.rst file.
* Numerous bug fixes.
* Python 3.5 fixes.
* PF fixes, especially for BSD.
