Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
  end
  config.vm.provision "ansible" do |user|
    user.playbook = "user.yml"
  end
  config.vm.provision "ansible" do |kafka|
    kafka.playbook = "kafka.yml"
    kafka.host_vars = {
      "kafka1" => {"brokerid" => 0,
                  "zookc" => "192.168.33.10:2181"},
      "kafka2" => {"brokerid" => 1,
                  "zookc" => "192.168.33.10:2181"}
    }
  end
  config.vm.define "kafka1" do |kafka1|
    kafka1.vm.box = "ubuntu/trusty64"
    kafka1.vm.network :private_network, ip: "192.168.33.10"
  end

  config.vm.define "kafka2" do |kafka2|
    kafka2.vm.box = "ubuntu/trusty64"
    kafka2.vm.network :private_network, ip: "192.168.33.11"
  end
end


