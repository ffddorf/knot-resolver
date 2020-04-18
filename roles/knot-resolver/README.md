Knot Resolver
=========

A DNS Resolver using software from the Knot project.

Requirements
------------

none

Role Variables
--------------

`kresd_instances` the number of service instances to start (default: 2)

Dependencies
------------

none

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: dns-resolvers
      roles:
         - { role: knot-resolver, kresd_instances: 3 }

License
-------

MIT

Author Information
------------------

Freifunk Düsseldorf e.V. <kontakt@freifunk-duesseldorf.de>
