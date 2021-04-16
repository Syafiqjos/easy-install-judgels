# Easy Install Judgels VM
Quick and Easy install Judgels (Judgement Angels)

Judgels Source : [Judgels Github](https://github.com/ia-toki/judgels)

## Install Judgels
Reference : [Judgels Installation Guide](https://github.com/ia-toki/judgels/wiki/Installation-Guide:-Deployment)

### 0. Install requirement
```
sudo apt install ansible net-tools
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
```

### 7. Check ip
```
ifconfig
```

### 8. Edit hosts
```
vim dist/hosts
```

### 8. Edit localhost to ip and save

example
```
[local]
localhost

[judgels]
1.2.3.4 ansible_user=root

[database]
1.2.3.4 ansible_user=root

[raphael]
1.2.3.4 ansible_user=root

[jophiel]
1.2.3.4 ansible_user=root

[sandalphon]
1.2.3.4 ansible_user=root

[sealtiel]
1.2.3.4 ansible_user=root

[uriel]
1.2.3.4 ansible_user=root

[gabriel]
1.2.3.4 ansible_user=root

[scoreboard_receiver]
1.2.3.4 ansible_user=root
```

### 9. 