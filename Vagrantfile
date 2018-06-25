Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "192.168.100.10"
  config.vm.synced_folder "./", "/app"
  config.vm.provision "shell", inline: <<-SHELL
        cd /tmp
        sudo yum update
        sudo yum -y install python-setuptools python2.7 python-simplejson gcc libssl-dev python-dev wget
        sudo wget https://bootstrap.pypa.io/get-pip.py 
        sudo python get-pip.py
        sudo pip install ansible
  SHELL
end