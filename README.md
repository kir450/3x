3x

ssh root@192.168.80.50

htop -  список запущенных процессов

reboot

#do-release-upgrade

sudo nano /etc/ssh/sshd_config

Port 10022

sudo systemctl daemon-reload

sudo systemctl restart ssh

ss -ntpl

sudo ufw enable && ufw allow 10022/tcp

ufw status numbered

nano /etc/ufw/before.rules

# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP

# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-forward -p icmp --icmp-type echo-request -j DROP

ufw disable && ufw enable

sudo apt-get install curl

curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash

sudo apt-get install speedtest

grep -r 'ookla' /etc/apt/

rm /etc/apt/keyrings/ookla_speedtest-cli-archive-keyring.gpg

rm /etc/apt/sources.list.d/ookla_speedtest-cli.list

или

apt install python3-venv

python3 -m venv venv

source venv/bin/activate

pip install speedtest-cli

speedtest-cli

deactivate


bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)

ufw allow 6555/tcp

ufw allow 443/tcp

SSH-тунель для адинки 3x-ui

ss -ntpl

LISTEN 0      4096       127.0.0.1:6555         0.0.0.0:*     users:(("x-ui",pid=941,fd=3))

MobaXterm-Tunneling-New SSH tunnel


