Bootstrap: docker
From: openfoam/openfoam5-paraview54:latest

%post
    # Setup a very minimal bashrc file
    mkdir -p /opt
    echo 'PS1="Singularity \w> "' > /opt/bashrc

%environment
    source /opt/openfoam5/etc/bashrc

%runscript
    echo "Welcome to the OpenFOAM Singularity container!"
    
    # Disable annoying sudo message
    touch ~/.sudo_as_admin_successful
    
    exec /bin/bash --rcfile /opt/bashrc "$@"
