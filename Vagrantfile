Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.provider "virtualbox" do |v|
      v.memory = 8192
      v.cpus = 4
    end
    config.vm.hostname = "tract.local"
    config.vm.network "forwarded_port", guest: 4000, host: 4000
    config.vm.network "forwarded_port", guest: 35729, host: 35729
    config.vm.network "private_network", ip: "192.168.33.10"
    config.vm.synced_folder ".", "/tractio"
    config.vm.provision "shell", inline: <<-SHELL
        sudo apt update
        sudo apt upgrade -y
        sudo apt install ruby-full build-essential zlib1g-dev -y
        echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
        echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
        echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
        source ~/.bashrc
        gem install jekyll bundler
    SHELL
end