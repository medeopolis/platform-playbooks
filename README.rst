Playbooks to set up / configure infrastructure and services.

**This repository assumes Ansible is installed and configured**

The following directories contain Playbooks with specific duties:
deployment - Creating VMs, VPCs, Load balancers, other
            infrastructurey things
platform - Management and configuration of the OS / settings of a deployed
            VM/LB/VPC/...
decommission - Destroying resources created by 'deployment' scripts in an
            orderly way.

Note applications will have their own role/collection in a separate repository.


Installing
==========

Ansible configuration including inventory is stored elsewhere except
information about roles and collections required to run these playbooks, which
is in this repository.

Some (actually most) collections will have extra python packages they require
to function. These can be installed from requirements.txt.

::

  pip install -r requirements.txt


Install any desired Ansible collections; this command installs all collections
required for the playbooks in this repository.

::

  ansible-galaxy collection install -r requirements.yam


Other setup
===========

None at this time.

Service specific notes
======================


Binary Lane
-----------

NOTE: as of November 2022 it was confirmed by Binary Lane support that they are
no longer supporting their OpenStack API and that 2023 it will be replaced
entirely by their new OpenAPI based API.
The last known compatible Nova client was python-novaclient V4 from OpenStack
Neuton.
Still outstanding is the question of if they will provide an Ansible
collection to support their cloud.

Because of this they have been removed until their integration improves.

Vultr
-----

* `Enable Vultr API`.. then create API Key
* Ensure your IP address/s are in the Access Control list
* Set an Ansible variable vultr_api_key; this is used by
  deployment/test-vultr.yaml and deployment/build-vultr-resource-stack.yaml

.. _`Enable Vultr API`: https://my.vultr.com/settings/#settingsapi

