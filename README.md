# Apache RPAF (`apache-rpaf`)

**Part of the BAS Ansible Role Collection (BARC)**

Configures Apache to use the Reverse Proxy Add Forward module

## Overview

* Restarts Apache to pick up RPAF module
* Creates an includes file containing module configuration and loads this within the default virtual host

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

* `apache`

### Variables

* `apache_rpaf_config_file_path`
    * Path consisting of directory and file name for the file that will contain this module's configuration options
    * This variable **MUST** be a valid UNIX path and **SHOULD NOT** exist.
    * Default: "/etc/apache2/conf-available/mod-rpaf.conf"
* `apache_rpaf_option_enable`
    * If "On" the RPAF engine will be enabled
    * See the [module documentation](https://github.com/gnif/mod_rpaf#configuration-directives) for more information.
    * You **MUST** quote this value or Ansible will evaluate this value to a "True" or "False" which are not valid.
    * Allowed values: "on" or "off".
    * Default: "On"
* `apache_rpaf_option_set_hostname`
    * Update Update vhost name so ServerName & ServerAlias work
    * See the [module documentation](https://github.com/gnif/mod_rpaf#configuration-directives) for more information.
    * You **MUST** quote this value or Ansible will evaluate this value to a "True" or "False" which are not valid.
    * Allowed values: "on" or "off".
    * Default: "On"
* `apache_rpaf_option_proxy_ips`
    * What IPs & bitmaksed subnets to adjust requests for
    * See the [module documentation](https://github.com/gnif/mod_rpaf#configuration-directives) for more information.
    * By default this variable will be the IPv4 address of the local interface.
    * You **SHOULD NOT** need to change this value.
    * Default: "{{ ansible_lo.ipv4.address }}"

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) workflow is used to manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* (where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2015 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.