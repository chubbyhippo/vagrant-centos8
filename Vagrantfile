Vagrant.configure("2") do |config|
    config.vm.box = "centos/8"
    config.vm.box_version = "1905.1"
    config.vm.network "forwarded_port", guest: 800, host: 8000
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf update -y
      sudo dnf group install "Development Tools" -y
      sudo dnf install vim tmux -y
      sudo runuser -l vagrant -c "curl https://raw.githubusercontent.com/chubbyhippo/vimrc/master/.vimrc -o ~/.vimrc"
      sudo runuser -l vagrant -c "ssh-keygen -t ed25519 -f /home/vagrant/.ssh/id_ed25519 -q -N ''"

      # install python
      sudo dnf install python3 python3-devel -y
      sudo runuser -l vagrant -c "python3 -m venv ~/env"
      
      # install java
      sudo dnf install java -y

      # install nodejs
      curl -sL https://deb.nodesource.com/setup_12.x | bash -
      sudo dnf install nodejs -y
      
      # install angular cli
      sudo npm install -g @angular/cli

    SHELL
   end
