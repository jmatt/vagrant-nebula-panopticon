vagrant-nebula-panopticon
=========================

A Vagrant configuration backed by NCSA's Nebula OpenStack cloud to provide Panopticon.

Topology
--------

The Vagrantfile creates the minimal system configuration. This current uses seven VMs.

The naming used by the Vagrantfile provides a specific nomenclature. This only provides semantics for humans, but may still be useful. All servers begin with p to denote that it's part of Panopticon. Servers containing es provide Elasticsearch. Odd Elasticsearch servers are data and client servers. Even Elasticsearch servers are masters. The lfr server provides Logstash, FluentD and Riemann.

Use
---

This repository is based on [vagrant-nebula](https://github.com/lsst-sqre/vagrant-nebula). There is great documentation provided by the [LSST SQuaRE vagrant-nebula README](https://github.com/lsst-sqre/vagrant-nebula).


```
vagrant up
```

Create the minimal Panopticon system.

```
vagrant ssh p-es-k
```

SSH to a specific machine. This machine has Elasticsearch and Kibana.

More Resources
--------------

https://github.com/lsst-sqre/vagrant-nebula - The vagrant-nebula repository.

https://www.vagrantup.com/ - The Vagrant homepage.

https://nebula.ncsa.illinois.edu - The NCSA Nebula OpenStack Horizon dashboard.

https://github.com/ggiamarchi/vagrant-openstack-provider - The Vagrant plugin that vagrant-nebula uses.

http://ls.st/ug - LSST Software Stack documentation.

https://github.com/lsst-sqre/asteroid - Use libcloud to interact with Nebula.

https://github.com/openstack/python-openstackclient - The OpenStack command-line client.
