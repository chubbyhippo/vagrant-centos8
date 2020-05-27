Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  config.vm.box_version = "1905.1"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.provision "shell", inline: <<-SHELL
    sudo dnf update -y
    sudo dnf group install "Development Tools" -y
    sudo dnf install vim tmux python3 python3-devel java -y
    sudo runuser -l vagrant -c "python3 -m venv ~/env"
    sudo runuser -l vagrant -c "ssh-keygen -b 2048 -t rsa -f /tmp/sshkey -q -N ''"
    curl https://raw.githubusercontent.com/chubbyhippo/vimrc/master/.vimrc -o /home/vagrant/.vimrc
  SHELL
 end
