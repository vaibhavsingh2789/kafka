Vagrant.configure("2") do |config|
  config.vm.provision "ansible" do |user|
    user.playbook = "user.yml"
    user.inventory_path="inventory"
  end
  config.vm.provision "ansible" do |kafka|
    kafka.playbook = "kafka.yml"
    kafka.inventory_path="inventory"
  end
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu14.04"
    web.vm.network :private_network, ip: "192.168.33.10"
  end

  config.vm.define "db" do |db|
    db.vm.box = "ubuntu14.04"
    db.vm.network :private_network, ip: "192.168.33.11"
  end
end


