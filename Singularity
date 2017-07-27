Bootstrap: docker
From: ubuntu:16.04

%post
    # Setup a very minimal bashrc file
    mkdir -p /opt
    echo 'PS1="Singularity \w> "' > /opt/bashrc

    # Install apt-add-repository command
    apt-get update
    apt-get -y --with-new-pkgs -o Dpkg::Options::="--force-confold" upgrade
    apt-get -y install software-properties-common
    
    # Universe repository needed for OpenFOAM
    apt-add-repository universe
    apt-get update
    
    # Add OpenFOAM repository
    add-apt-repository http://dl.openfoam.org/ubuntu
    wget -O - http://dl.openfoam.org/gpg.key | apt-key add -
    apt-get update

    # SSH client is needed for OpenMPI
    apt-get -y install ssh
    apt-get -y install openmpi

    # Install OpenFOAM + some nice to have utilities
    apt-get -y install python-numpy python-scipy python-matplotlib python-ipython ipython python-h5py
    apt-get -y install openfoam5
    apt-get -y -o Dpkg::Options::="--force-confold"  dist-upgrade

%environment
    source /opt/openfoam5/etc/bashrc

%runscript
    echo "Welcome to the OpenFOAM Singularity container!"
    
    # Disable annoying sudo message
    touch ~/.sudo_as_admin_successful

    exec /bin/bash --rcfile /opt/bashrc "$@"
