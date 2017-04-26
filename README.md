# run-devstack-via-lxc

Create a container to run devstack

    sudo lxc-create -t ubuntu -n devstack -f devstack-lxc.conf -- \
        --packages=bsdmainutils,git,ca-certificates --release xenial --arch=amd64

Start and connect via ssh

    sudo lxc-start -n devstack
    ssh ubuntu@$(sudo lxc-info -n devstack | awk '/IP/ { print $2 }')) #password ubuntu

[Install devstack](https://docs.openstack.org/developer/devstack/guides/single-machine.html)