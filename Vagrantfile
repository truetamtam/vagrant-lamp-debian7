# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.box = "debian-70"
  config.vm.box_url = "http://domain.com/path/to/above.box"


  config.vm.network :hostonly, "11.11.11.11"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.synced_folder "./", "/var/www"

  config.vm.forward_port 3306, 33066
  config.vm.forward_port 22, 2222

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
