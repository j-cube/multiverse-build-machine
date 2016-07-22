# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "puppetlabs/centos-6.6-64-nocm"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
    # Customize the amount of memory on the VM:
  #  vb.memory = "1024"
  end

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
  
    # Customize the amount of memory on the VM:
    vb.memory = "1280"
  end

  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL

  config.vm.provision "shell", inline: <<-SHELL
    sudo rpm --import http://ftp.scientificlinux.org/linux/scientific/5x/x86_64/RPM-GPG-KEYs/RPM-GPG-KEY-cern
    sudo wget -O /etc/yum.repos.d/slc6-devtoolset.repo http://linuxsoft.cern.ch/cern/devtoolset/slc6-devtoolset.repo
    # sudo yum -y install devtoolset-2
    sudo yum -y install devtoolset-2-toolchain devtoolset-2-binutils devtoolset-2-gcc devtoolset-2-gcc-c++ devtoolset-2-gcc-gfortran
    echo "source /opt/rh/devtoolset-2/enable" >> ~/.bashrc
    sudo echo "source /opt/rh/devtoolset-2/enable" >> /root/.bashrc
    source /opt/rh/devtoolset-2/enable
    sudo yum -y install cmake git bzip2 patch
    sudo yum -y install zlib-devel libjpeg-devel libtiff-devel libpng-devel
    sudo yum -y install python-devel python-setuptools numpy
    sudo yum -y install readline-devel sqlite-devel pcre pcre-devel ncurses-devel openssl-devel db4-devel gdbm-devel bzip2-devel
    sudo yum -y install cloog-ppl cloog-ppl-devel
    sudo yum -y install mesa-libGL-devel mesa-libGLU-devel freeglut freeglut-devel libXmu-devel libXi-devel glew-devel
    sudo rpm -Uvh http://www.city-fan.org/ftp/contrib/yum-repo/city-fan.org-release-1-13.rhel6.noarch.rpm
    wget http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    sudo rpm -ivh epel-release-6-8.noarch.rpm
    #sudo yum -y upgrade curl
    sudo yum -y clean all
    sudo yum -y install wget libcurl curl nano mg
    sudo yum -y install tcl

    sudo groupadd developers
    sudo usermod -a -G developers vagrant

    if [ ! -e alembic-builder ] ; then
      git clone https://github.com/j-cube/alembic-builder
    fi
    cd alembic-builder
    git checkout linux-gcc48-multiverse-2.0.0
    perl -pi -e 's/wget --content-disposition/wget -q --content-disposition/' do-*.sh
    # fix temp problem on github for msgpack
    perl -pi -e 's/wget -q --content-disposition/wget -q/' do-build-msgpack.sh
    source env-build-setup.sh
    ./do-build-all.sh
  SHELL
end
