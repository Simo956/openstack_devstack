# openstack_devstack
openstack commands installation ubuntu

    sudo apt install net-tools
    sudo apt-add-repository universe
    sudo apt-get update && sudo apt upgrade
    sudo apt install git
    sudo apt-get install ntp
    sudo apt install open-vm-tools && sudo apt install open-vm-tools-desktop
    sudo apt-get install iptables && sudo apt-get install arptables && sudo apt-get install ebtables
    sudo apt install python3-pip
    sudo update-alternatives --set iptables /usr/sbin/iptables-legacy || true
    sudo update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy || true
    sudo update-alternatives --set arptables /usr/sbin/arptables-legacy || true
    sudo update-alternatives --set ebtables /usr/sbin/ebtables-legacy || true
    /usr/bin/python3.10 -m pip install --upgrade pip
    sudo rm -rf /usr/lib/python3/dist-packages/yaml
    sudo rm -rf /usr/lib/python3/dist-packages/PyYAML-*
    sudo rm -rf /usr/lib/python3/dist-packages/simplejson*
    sudo useradd -s /bin/bash -d /opt/stack -m stack
    sudo chmod +x /opt/stack
    echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
    sudo -u stack -i
    git clone https://opendev.org/openstack/devstack
    exit
    sudo chown -R stack:stack /opt/stack/devstack
    sudo /opt/stack/devstack/tools/create-stack-user.sh
    sudo -u stack -i
    cd devstack
    sudo cp samples/local.conf local.conf
    sudo nano local.conf
    export XDG_SESSION_TYPE=wayland
    sudo mkdir /opt/stack/logs/
    sudo touch /opt/stack/logs/error.log
    sudo chown stack:stack /opt/stack/logs/error.log
    sudo chown -R stack:stack /opt/stack
    FORCE=yes ./stack.sh
