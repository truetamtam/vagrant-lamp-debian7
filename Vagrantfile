# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "debian-70"
  # config.vm.box_url = "https://static.nls.io/debian-70.box"

  config.vm.network "private_network", ip: "11.11.11.11"
  config.vm.synced_folder "./", "/var/www"

  config.vm.network "forwarded_port", guest: 3306, host: 33066
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provision :chef_solo do |chef|
   chef.cookbooks_path = "vagrant/cookbooks"
   chef.data_bags_path = "vagrant/data_bags"
   chef.add_recipe "apt"
   chef.add_recipe "apache2"
   chef.add_recipe "php"
   chef.add_recipe "openssl"
   chef.add_recipe "git"
   chef.add_recipe "mysql"
   chef.add_recipe "vagrant_main"
  
   # You may also specify custom JSON attributes:
   chef.json.merge!({
     "mysql" => {
       "server_root_password" => "111",
       "server_repl_password" => "111",
       "server_debian_password" => "111",
       "bind_address" => "0.0.0.0"
     }
   })
  end


end
