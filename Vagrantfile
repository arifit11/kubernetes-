Vagrant.configure(2) do |config|
  config.hostmanager.enabled = true
  config.vm.box = "centos/7"
  ssh_pub_key = File.readlines("/Users/arif.khan/.ssh/id_rsa.pub").first.strip

  # control
  config.vm.define "k8s-Master", primary: true do |h|
    h.vm.network "private_network", ip: "192.168.135.10"
    h.vm.provider :virtualbox do |ps|
      ps.memory = 1024
      ps.name = "vb-k8s-Master"
    end
    h.vm.provision 'shell', inline: 'mkdir -p /root/.ssh'
    h.vm.provision 'shell', inline: "echo #{ssh_pub_key} > /root/.ssh/authorized_keys"
    h.vm.provision 'shell', inline: 'chmod 600 /root/.ssh/authorized_keys'
    h.vm.provision 'shell', inline: 'chmod 700 /root/.ssh'
    end
    config.vm.define "k8s-worker" do |h|
    h.vm.network "private_network", ip: "192.168.135.101"
    h.vm.provider :virtualbox do |ps|
      ps.memory = 512
      ps.name = "vb-k8s-worker"
    end
    h.vm.provision 'shell', inline: 'mkdir -p /root/.ssh'
    h.vm.provision 'shell', inline: "echo #{ssh_pub_key} > /root/.ssh/authorized_keys"
    h.vm.provision 'shell', inline: 'chmod 600 /root/.ssh/authorized_keys'
    h.vm.provision 'shell', inline: 'chmod 700 /root/.ssh'
    #h.vm.provision "ansible" do |ansible|
    #  ansible.playbook = "repo/sensu-client.yml"
    #end

    end
end
