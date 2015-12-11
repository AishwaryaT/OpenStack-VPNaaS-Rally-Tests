Welcome!
========

This contains the rally test codes for the Neutron VPN as a Service (VPNaaS) service. The tests
currently require rally to be installed via devstack or standalone. It is assumed that you
also have Neutron with the Neutron VPNaaS service installed.

These tests could also be run against a multinode openstack.

Please see /neutron-vpnaas/devstack/README.md for the required devstack configuration settings
for Neutron-VPNaaS.

Structure:
==========

1. plugins - Directory where you can add rally plugins. Almost everything in Rally is a plugin.
Contains base, common methods and actual scenario tests
2. rally-configs - Contains input configurations for the scenario tests

How to test:
============

Included in the repo are rally tests. For information on rally, please see the rally README :

https://github.com/openstack/rally/blob/master/README.rst

* Create a rally deployment for your cloud and make sure it is active.
  rally deployment create --file=cloud_cred.json --name=MyCloud
* Create a folder structure as below
   sudo mkdir /opt/rally
* Create a symbolic link to the plugins directory
   cd /opt/rally
   sudo ln -s /opt/stack/neutron-vpnaas/rally-jobs/plugins
* Update the args.json file with the correct credentials
* Run the tests
  With DVR:
   rally task start /opt/stack/neutron-vpnaas/rally-jobs/rally-configs/rally_config_dvr.yaml
   --task-args-file /opt/stack/neutron-vpnaas/rally-jobs/rally-configs/args.json

  Non DVR:
  rally task start /opt/stack/neutron-vpnaas/rally-jobs/rally-configs/rally_config_non_dvr.yaml
   --task-args-file /opt/stack/neutron-vpnaas/rally-jobs/rally-configs/args.json

External Resources:
===================

For more information on the rally testing framework see: <https://github.com/openstack/rally>
