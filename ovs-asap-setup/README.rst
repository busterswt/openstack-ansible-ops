Open vSwitch ASAP^2 Tools
#########################
:date: 2019-02-26
:tags: openstack, ansible
:category: \*openstack, \*nix

About this repository
---------------------

The tools found here are meant to assist the OpenStack-Ansible
operator with deploying Open vSwitch capable of offloading
flows to hardware using ASAP :sup:`2` technology from Mellanox.

The documentation outlining the full installation process can be
found here:

`<https://docs.openstack.org/openstack-ansible-os_neutron/latest/app-openvswitch-asap.html>`_

Process
-------

The ``ovs-asap-setup.yaml`` playbook can be used to implement a
service that prepares the NIC for hardware offloading. Because
the changes do not persist a reboot, there service is set to run at
every boot.

The playbook relies on an existing OpenStack-Ansible inventory to determine
the provider network mappings, and performs the SR-IOV and offloading-related
on the respective network interfaces. Files and templates can be modified
to meet an operator's particular requirements.

Other tasks include:

* Create a networkd link file to ensure Mellanox cards using the ``mlx5_core``
  have consistent names based on slot location

To execute the playbook, perform the following command:

:code:`# openstack-ansible ovs-asap-setup.yaml`

Warranty
--------

There is none. Please review the playbook and associated files before
implementing in your environment and understand what is being done.
