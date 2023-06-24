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

There is an outstanding task to document the variables used by these playbooks.

Service specific notes
======================

OpenStack clouds
----------------

Openstack support has been tested on OVH Cloud (https://www.ovhcloud.com/) and
Nectar Research Cloud (https://nectar.org.au/).

The included playbooks assume clouds.yaml is in use but as long as the python
openstack bindings find a supported authentication mechanism things should work
ok.

Vultr
-----

* `Enable Vultr API`.. then create API Key
* Ensure your IP address/s are in the Access Control list
* Set an Ansible variable vultr_api_key; this is used by
  deployment/test-vultr.yaml and deployment/build-vultr-resource-stack.yaml

.. _`Enable Vultr API`: https://my.vultr.com/settings/#settingsapi


Licence
=======

These files are, in the main, developed by Medeopolis and released under the
terms of *GNU General Public License 3 or any later version*.

On any Debian derivative the full text of GNU GPL3 can be found in
/usr/share/common-licenses/GPL-3 or it can be viewed online at
https://www.gnu.org/licenses/gpl-3.0.en.html .

Where files are imported from a third party (either as a base or in whole) we
will endeavour to include their copyright notice here.

