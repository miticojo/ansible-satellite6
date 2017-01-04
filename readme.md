# Satellite 6.x Lab

Author: Giorgio Crivellari
Version: 0.2

This playbook handles Satellite installation for RHEL 6 and 7 using ISO or Red Hat network.

## Prerequisites
* Vagrant or dedicated fresh base RHEL 6.x/7.x installation
* SSH key preshared key present on target node
* Ansible 1.9 or 2.0+ installed
* Ansible inventory file filled with target address

## Target environment definition

Before running playbook you need to define some basic variables that will drive Satellite installation:

* fqdn_hostname: FQDN hostname of target machine (it MUST be like this: satellite.domain.loc)
* rhn_user: Red Hat Network credentials
* rhn_pass: ****
* install_sos: Install SOS Report package for support purpose (True/False)
* local_iso_path: If ISO path is set force installation through local media
* remote_iso_path: Target path where ISO is copied (check space availability)
* remote_iso_mount: Target mount there ISO is mounted
* foreman_initial_organization: Organization name
* foreman_initial_location: Location name for organization defined before
* foreman_admin_username: Administrator credentials for Satellite
* foreman_admin_password: ******

## Tested on
Playbook has been tested on

| OS | ISO | RH Network |
|----|-----|------------|
| 7.x | Y | N |
| 6.x | N | N |

## Improvements

* Separate disk management for PULP contents
* Capsule installation only
* First setup:
  * import RH manifest if installation succeeds
  * setup RH base product
  * setup sync schedule
