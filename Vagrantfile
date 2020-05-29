Vagrant.configure("2") do |config|
    config.vm.box = "centos/8"
    config.vm.box_version = "1905.1"
    config.vm.synced_folder ".", "/vagrant", disabled: true
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
      sudo runuser -l vagrant -c "mkdir ~/.npm-global"
      sudo runuser -l vagrant -c "npm config set prefix '~/.npm-global'"
      sudo runuser -l vagrant -c "echo 'export PATH=~/.npm-global/bin:$PATH' > ~/.profile"
      sudo runuser -l vagrant -c "source ~/.profile"
      
      # install angular cli
      npm install -g @angular/cli

    SHELL
   end
