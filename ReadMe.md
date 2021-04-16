# Easy Install Judgels VM
Quick and Easy install Judgels (Judgement Angels)

Judgels Source : [Judgels Github](https://github.com/ia-toki/judgels)

## Install Judgels
Reference : [Judgels Installation Guide](https://github.com/ia-toki/judgels/wiki/Installation-Guide:-Deployment)

### 0. Install requirement
```
sudo apt install ansible net-tools sshpass python3-pip
```

### 1. Initialize
```
cd ~
```

### 2. Download Judgels
```
git clone https://github.com/ia-toki/judgels
```

### 3. Go to judgels/deployment/ansible
```
cd ~/judgels/deployment/ansible
```

### 4. Copy dist-example into home
```
cp -r dist-example ~/judgels-deployment
```

### 5. Create symlink
```
 ln -s ~/judgels-deployment dist
```

### 6. Manage root user (on interpreter choose a password) and edit ssh
```
sudo passwd root
#Enter password

sudo vim /etc/ssh/sshd_config

#find this line :
#PermitRootLogin prohibit-password
#change it to
#PermitRootLogin yes
#then save

systemctl restart sshd
```

### 7. Check ip
```
ifconfig
```

### 8. Edit hosts
```
vim dist/hosts
```

### 8. Edit localhost to ip and save (some example)

```
[local]
localhost

[judgels]
192.168.233.133 ansible_user=root

[database]
192.168.233.133 ansible_user=root

[raphael]
192.168.233.133 ansible_user=root

[jophiel]
192.168.233.133 ansible_user=root

[sandalphon]
192.168.233.133 ansible_user=root

[sealtiel]
192.168.233.133 ansible_user=root

[uriel]
192.168.233.133 ansible_user=root

[gabriel]
192.168.233.133 ansible_user=root

[scoreboard_receiver]
192.168.233.133 ansible_user=root
```

### 9. Modify and Run ansible-playbook
```
#modify provision-machine.yml
vim playbooks/provision-machine.yml
```

```
#change line to this
raw: test -e /usr/bin/python3 || (apt -y update && apt install -y python3-minimal python3-pip)
```

```
sudo ansible-playbook -e @dist/env.yml playbooks/provision-machine.yml --ask-pass
#then type root password
```

## References
- https://www.liquidweb.com/kb/enable-root-login-via-ssh/
- https://www.cyberciti.biz/faq/change-root-password-ubuntu-linux/