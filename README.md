Vagrant/Puppet setup for sf2 install
==============================================================

puPHPet generated vagrant/puppet bundle altered to provide a quick and easy sf2 setup.

This setup provides:
* debian 64bit squeeze
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
* symfony 2.3.1

Installation
------------
    git clone https://github.com/ftdysa/symfony-vagrant.git
    cd symfony-vagrant
    customize config
    vagrant up
    vagrant ssh
  
At this point you should be ssh'd into the VM. To browse to the sites hosted on the VM from your desktop, open /etc/hosts and add the following lines (replace with values from config):

    $vm_ip $vhost www.$vhost
    $vm_ip $sfvhost www.$sfvhost
    $vm_ip $xhprofvhost www.$xhprofvhost
    
After commenting out the localhost checks in $docroot/symfony/web/app_dev.php you should be able to load $sfvhost/app_dev.php in your browser.
