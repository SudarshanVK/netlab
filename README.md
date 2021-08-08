<!--
# Development Notes

This is development branch for what might become release 0.8 or release 0.7.1 (depending on how many changes we'll accumulate in this release).
-->

# Overview

*netsim-tools* are bringing infrastructure-as-code concepts to networking labs. You'll describe your high-level network topology and routing design in a YAML file, and the tools in this repository will

* Create *Vagrantfile* configuration file for *virtualbox* or *libvirt* environment
* Create *containerlab* configuration file
* Create Ansible inventory and configuration file
* Create IPv4 and IPv6 addressing plan and OSPF, EIGRP, IS-IS, and BGP routing design
* Configure IPv4, IPv6, LLDP, OSPF, EIGRP, IS-IS, BGP, or SR-MPLS on your lab devices.

Instead of wasting time creating lab topology in a GUI and configuring boring details, you'll start with a lab preconfigured according to your specifications.

## Releases

* Latest release: [release_0.8.1](https://github.com/ipspace/netsim-tools/releases/tag/release_0.8.1) (read [release notes](https://netsim-tools.readthedocs.io/en/latest/release/0.8.html))
* If you find bugs in the 0.8 release, please report them and use the [release 0.7](https://github.com/ipspace/netsim-tools/releases/tag/release_0.7).

More details in [release notes](https://netsim-tools.readthedocs.io/en/latest/release.html).

You might also want to [read the documentation](https://netsim-tools.readthedocs.io/), and [installation guidelines](https://netsim-tools.readthedocs.io/en/latest/install.html).

## An overview of tools:

**netlab create**
: Creates a full-blown network topology, Vagrantfile and Ansible inventory from a simple list of nodes and links. [More details](https://netsim-tools.readthedocs.io/en/latest/netlab/create.html)

**netlab initial**
: Using topology data generated by **netlab create** and default device configuration templates configures common device parameters, protocols that should have been enabled (LLDP, OSPF, IS-IS, BGP, SR-MPLS), enables interfaces, and configures IP addresses on interfaces. [More details](https://netsim-tools.readthedocs.io/en/latest/netlab/initial.html)

**netlab config**
: Applies any Jinja2 configuration templates to network devices.

**netlab collect**
: Using Ansible fact gathering or other device-specific Ansible modules, collects device configurations and saves them in specified directory (default: **config**).

**netlab connect**
: Use SSH or **docker exec** to connect to a lab device using device names, management network IP addresses (**ansible_host**), SSH port, and username/passwords from Ansible inventory. Ideal when you use centralized Vagrant environments and want to connect to the devices while being in playbook development directory.

## Libvirt-specific tools

**enable-lldp.sh**
: Given libvirt network name, change group_fwd_mask for the corresponding Linux bridge to enable LLDP passthrough across the Linux bridge.
