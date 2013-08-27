Vagrant/Puppet setup for sf2 install
==============================================================

puPHPet generated vagrant/puppet bundle altered to provide a quick and easy sf2 setup.

Initial commit has no configuration setup so you'll want to edit Vagrantfile / manifests/default.pp
to change where symfony is installed and what your vm is called. 

By default, the docroot is /var/www which is NFS mounted to ./shared.

Symfony is installed to /var/www/symfony.

xhProf is installed to /var/www/xhprof

This setup provides:
* debian squeeze
* php 5.4
* git-core
* curl
* mysql 5.5
* php5-curl
* php5-cli
* php5-mcrypt
* php5-apc
* php5-intl
* build-essential
* vim
* vim-common
* vim-scripts

