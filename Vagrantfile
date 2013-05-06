# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.box = "debian-70"
  # config.vm.box_url = "http://domain.com/path/to/above.box"


  config.vm.network :hostonly, "33.33.33.40"

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
       "server_root_password" => "vagrant",
       "server_repl_password" => "vagrant",
       "server_debian_password" => "vagrant",
       "bind_address" => "0.0.0.0"
     }
   })
  end


end
