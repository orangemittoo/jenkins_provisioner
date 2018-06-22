Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.define "target" do |node|
        node.vm.box = "centos/7"
        node.vm.hostname = "target"
        node.vm.network :private_network, ip: "192.168.100.20"
        node.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2220
  end
  config.vm.provision "shell", inline: <<-SHELL
        cd /tmp
        sudo yum update
        sudo yum -y install python-setuptools python2.7 python-simplejson gcc libssl-dev python-dev wget
        sudo wget https://bootstrap.pypa.io/get-pip.py 
        sudo python get-pip.py
        sudo pip install ansible
        ansible-playbook site.yml
  SHELL
end