Playbooks to set up / configure infrastructure and services.

**This repository assumes Ansible is installed and configured**

The following directories contain Playbooks with specific duties:
deployment - Creating VMs, VPCs, Load balancers, other infrastructurey things
platform - Management and configuration of the OS / settings of a deployed
            VM/LB/VPC/...

Note applications will have their own role/collection in a separate repository.

Ansible configuration including inventory is stored elsewhere except
information about roles and collections required to run these playbooks, which
is in this repository.

Install any desired Ansible collections; this command installs all collections
required for the playbooks in this repository.

::

  ansible-galaxy install -r requirements.yml

