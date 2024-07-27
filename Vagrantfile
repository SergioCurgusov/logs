Vagrant.configure("2") do |config|
    # Base VM OS configuration.
    config.vm.box = "bento/ubuntu-22.04"
    config.vm.provider :virtualbox do |v|
      v.memory = 1512
      v.cpus = 2
    end
  
    # Define two VMs with static private IP addresses.
    boxes = [
      { :name => "web",
        :ip => "192.168.56.10",
      },
      { :name => "log",
        :ip => "192.168.56.15",
      }
    ]
    # Provision each of the VMs.
    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.network "private_network", ip: opts[:ip]
        if opts[:name] == boxes.last[:name] 
          config.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/playbook.yml"
            #ansible.inventory_path = "ansible"
            ansible.become = "true"
            ansible.host_key_checking = "false"
            ansible.limit = "all"
          end
        end
  
      end
    end
end