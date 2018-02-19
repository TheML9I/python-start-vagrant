Vagrant.configure("2") do |config|
  config.vm.define "dev" do |srv|
    srv.vm.box = "ubuntu/trusty64"
    srv.vm.box_check_update = false
    srv.vm.hostname = 'python.class'
    srv.vm.network "private_network", ip: '192.168.99.49', :netmask => "255.255.255.0"
    srv.vm.provider :virtualbox do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end

    # Run Ansible from the Vagrant VM
    srv.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/site.yml"
      ansible.verbose = true
      ansible.install = true
      ansible.limit = "all"
      ansible.inventory_path = "ansible/inventory/development"
    end
  end
end