config = File.expand_path("../config", __FILE__)
load config

Vagrant.configure("2") do |config|
  config.vm.box = $vm_name
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/debian-607-x64-vbox4210.box"

  config.vm.network :private_network, ip: $vm_ip
    config.vm.network :forwarded_port, guest: $guest_port, host: $host_port
    config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--name", $vm_name]
  end

  nfs_setting = RUBY_PLATFORM =~ /darwin/ || RUBY_PLATFORM =~ /linux/
  config.vm.synced_folder $sync_source, $sync_target, id: "vagrant-root" , :nfs => nfs_setting
  config.vm.provision :shell, :inline =>
    "if [[ ! -f /apt-get-run ]]; then sudo apt-get update && sudo touch /apt-get-run; fi"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.module_path = "modules"
    puppet.options = ['--verbose']
    puppet.facter = {
        "mysql_user" => $mysql_user,
        "mysql_pass" => $mysql_pass,
        "vhost"      => $vhost,
        "docroot"    => $docroot,
        "sfvhost"    => $sfvhost,
        "xhprofvhost" => $xhprofvhost
    }
  end
end
