htop -  список запущенных процессов


3x

useradd -m xxxui -G sudo -s /bin/bash

paswd xxxui 


sudo -l
(ALL : ALL) ALL

exit, su root(с паролем root), sudo -i (с парлем user)

ls -la

mkdir .ssh
cd .ssh
nano authorized_keys
chmod 600 authorized_keys

Закрвтие доступа по паролю root
nano /etc/ssh/sshd_config
PermitRootLogin no
PasswordAuthentication no
PermitEmptyPasswords no

Проверить: ls /etc/ssh/sshd_config.d/

systemctl restart sshd
если ругается то
systemctl restart ssh

bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)

54637

useradd -r -m rtunnel -s /bin/true

sudo -u rtunnel mkdir /home/rtunnel/.ssh


cd /home/rtunnel/.ssh

touch authorized_keys

chown rtunnel: authorized_keys

chmod 600 authorized_keys

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


