# Basic Setup of Ubuntu Server
- Install Ubuntu Server 22.04.1 LTS
    - https://ubuntu.com/download/server 
- Install Balena Etcher
    - https://www.balena.io/etcher 
- Put usb in your computer
- Flash Ubuntu to usb with Balena Etcher
- Put usb into computer you what to turn into a server
- Go to bios and change boot priority to usb
- Ubuntu Server Setup
    - Change Ubuntu-lv to use max volume to use all the storage
    - Enable install openssh server
- Ssh into server
    ```bash
    ssh [username]@[server ip]
    ```
    ```bash
    sudo apt update
    ```
    ```bash
    sudo apt upgrade
    ```
- Server Security
    - Use keys instead of password to ssh into server
    - On server type: 
        ```bash
        mkdir ~/.ssh && chmod 700 ~/.ssh 
        ```
    - On computer: 
        ```bash
        ssh-keygen -b 4096
        ```
        ```bash
        cd .ssh
        ```
        ```bash
        scp $env:USERPROFILE/.ssh/id_rsa.pub [username]@[server ip]:~/.ssh/authorized_keys
        ```
    - Remove password options, set new port
        ```bash
        sudo nano /etc/ssh/sshd_config
        ```
        - Uncomment and change
            - Port to [New Port]
            - AddressFamily any to inet
            - PermitRootLogin to no
            - PasswordAuthentication to no
        - Press Ctrl X then Y then Enter
        ```bash
        sudo systemctl restart sshd
        ```
        ```bash
        ssh [username]@[server ip] -p [The set new port number]
        ```
    - Setup Firewall
        ```bash
        sudo ss -tupln
        ```
        ```bash
        sudo apt install ufw
        ```
        ```bash
        sudo ufw allow [The set new port number]
        ```
        ```bash
        sudo ufw status
        ```
        ```bash
        sudo nano /etc/ufw/before.rules
        ```
        - Type right after # ok icmp codes for INPUT
            - -A ufw-before-input -p icmp --icmp-type echo-request -j DROP
        - Press Ctrl X then Y then Enter
        ```bash
        sudo reboot
        ```
