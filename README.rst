Playbooks to set up / configure infrastructure and services.

**This repository assumes Ansible is installed and configured**

The following directories contain Playbooks with specific duties:
deployment - Creating VMs, VPCs, Load balancers, other infrastructurey things
platform - Management and configuration of the OS / settings of a deployed
            VM/LB/VPC/...

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

* `Create API key`..
* Check their `Openstack API Tutorial`.. for information about username and password.

.. _`Create API key`: https://home.binarylane.com.au/api-info
.. _`Openstack API Tutorial`: https://support.binarylane.com.au/support/articles/1000026198-openstack-command-line

I suggest making a clouds.yaml:

::

  mkdir $HOME/.config/openstack

Populate $HOME/.config/openstack/clouds.yaml with:

::

  clouds:
    binarylane:
      auth:
        auth_url: https://nova-api.binarylane.com.au/v2.0
        project_name: binarylane
        username: email address
        password: api key

Vultr
-----

* `Enable Vultr API`.. then create API Key
* Ensure your IP address/s are in the Access Control list
* Set an ansible variable vultr_api_key; this is used by deployment/test-vultr.yaml

.. _`Enable Vultr API`: https://my.vultr.com/settings/#settingsapi

