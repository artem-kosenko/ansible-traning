Vagrant.configure("2") do |config|
  config.vm.define     "vm1" do |host|
    # host.vm.provision :shell, :path => "shell/vm1.sh", run: "always"
    host.vm.box      = "centos/7"
    host.vm.hostname = "vm1.example.com"
    host.vm.network    "private_network",
      ip: "192.168.33.101",
      netmask: "255.255.255.0",
      auto_config: true,
      bootproto: "static"
    host.vm.provider   "virtualbox" do |vb|
      vb.name        = "vm1"
      vb.memory      = "2048"
      vb.cpus        = 1
    end
  end
end