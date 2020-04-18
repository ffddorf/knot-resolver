# Knot Resolver with Ansible

An Ansible role that installs a Knot Resolver service.

This code is for training purposes and not production ready.

## Description

We use the Ansible config management system to automate installation of a service.

Configuration is done by a template, which includes the primary IP addresses of the target system.

The whole process is automatically tested by Molecule. It runs on Docker to make tests quick.

The complicated part is where we run systemd inside a container to test the service supervisor.

## Preparation

We need to build a custom Docker image first. Inside the `role/knot-resolver/molecule` directory run the following:

```
docker build -t debian-systemd:10 .
```

## Usage

The whole building and testing process is automated in a single command. Go to the `role/knot-resolver` directory and run:

```
molecule test
```

## Development

Change the Ansible files freely and have Molecule apply them again with the following command:

```
molecule converge
```

## Role Variables

`kresd_instances` the number of service instances to start (default: 2)
`kresd_cachesize` size of the persisent resolver cache in MB (default: 100)
`kresd_prefix_ip4` restrict access to this IPv4 prefix (default: none)
`kresd_prefix_ip6` restrict access to this IPv6 prefix (default: none)

## Example Playbook

```
- hosts: dns-resolvers
  roles:
    - role: knot-resolver
      vars:
        kresd_instances: 3
        kresd_cachesize: 200
        kresd_prefix_ip4: 192.168.0.0/16
        kresd_prefix_ip4: fd00:1::/64
```

## License

MIT License

## Author Information

Freifunk Düsseldorf e.V. <kontakt@freifunk-duesseldorf.de>
