Vagrant.require_version ">= 2.1.2"
Vagrant.configure(2) do |config|

    # Set the default boot timeout
    config.vm.boot_timeout = 600

    # Use Ubuntu as base box
    config.vm.define "ubuntu" do |ubuntu|

        ubuntu.vm.box = "ubuntu/hirsute64"
        ubuntu.vm.hostname = "vagrant-mini-elastic-stack"
        ubuntu.vm.network :forwarded_port, guest: 5601, host: 5601

        # If you export the box switch to the second line to keep the /vagrant-mini-elastic-stack/ folder
        #ubuntu.vm.synced_folder "playbook/", "/playbook/"
        #ubuntu.vm.synced_folder "vagrant-mini-elastic-stack/", "/vagrant-mini-elastic-stack/", type: "rsync"
    end

    # increase amount of RAM for VirtualBox
    config.vm.provider "virtualbox" do |vb|
        vb.name = "vagrant-mini-elastic-stack"
        vb.customize [ "modifyvm", :id, "--memory", "3072" ]
    end

    # Configure the box with Ansible
    config.vm.provision "ansible_local" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible-playbook.yml"
    end


end
