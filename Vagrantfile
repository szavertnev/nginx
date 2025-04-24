Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  
  config.vm.define "web" do |web|
    web.vm.hostname = "web-server"
    web.vm.network "private_network", ip: "192.168.56.10"
    
    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory"
      ansible.extra_vars = {
        nginx_port: 8080
      }
      ansible.host_key_checking = false
      ansible.verbose = "v"
      ansible.limit = "web"
    end
  end
end