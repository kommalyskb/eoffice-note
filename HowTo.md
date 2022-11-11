# Install D-Office V3
ຕ້ອງຕິດຕັ້ງ Docker ກ່ອນ

## Install Docker for CentOS 8

Step 1: Go to the /etc/yum.repos.d/ directory.
```
cd /etc/yum.repos.d/
```
Step 2: Run the below commands
```
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
```
```
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```
Step 3: Now run the yum update
```
yum update -y
```
```
dnf update -y
```

Install Docker
```
dnf -y remove podman runc
```

```
curl https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo
```

```
sed -i -e "s/enabled=1/enabled=0/g" /etc/yum.repos.d/docker-ce.repo
```

```
dnf --enablerepo=docker-ce-stable -y install docker-ce
```

```
systemctl enable --now docker
```

```
rpm -q docker-ce
```
Test docker version
```
docker version
```

Install Docker Compose
```
curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```

```
chmod 755 /usr/local/bin/docker-compose
```
Test docker compose version
```
docker-compose --version
```

## Install Docker for CentOS 7
Step 1 — Installing Docker
```
sudo yum check-update
curl -fsSL https://get.docker.com/ | sh
sudo systemctl start docker
sudo systemctl status docker
sudo systemctl enable docker
```
Step 2 — Installing Docker Compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

```
sudo chmod +x /usr/local/bin/docker-compose
```
Test Version
```
docker-compose --version
```

## Install Docker for Ubuntu 20.04
Step 1 — Installing Docker
```
sudo apt update -y
```
```
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
```
apt-cache policy docker-ce
```
```
sudo apt install -y docker-ce
```
```
sudo systemctl status docker
```
```
sudo systemctl enable docker
```
```
sudo usermod -aG docker ${USER}
```
```
su - ${USER}
```
```
groups
```
Step 2 — Installing Docker Compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

```
sudo chmod +x /usr/local/bin/docker-compose
```
Test Version
```
docker-compose --version
```
## Install Docker for Ubuntu 22.04
Step 1 — Installing Docker CE
```
sudo apt update -y
```
```
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt update -y
```
```
apt-cache policy docker-ce
```
```
sudo apt install docker-ce -y
```
```
sudo systemctl status docker
```
```
sudo usermod -aG docker ${USER}
```
```
su - ${USER}
```
```
groups
```
Step 2 — Installing Docker Compose
```
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
```
```
chmod +x ~/.docker/cli-plugins/docker-compose
```
Test version
```
docker compose version
```

## 1. Setup Database

### ເຂົ້າໄປໃນ folder database ແລ້ວ Run command
```
docker-compose up -d
```
### ແລ້ວ Setup cluster single node
```
curl -X PUT http://admin:1qaz2wsx@127.0.0.1:5984/_users
curl -X PUT http://admin:1qaz2wsx@127.0.0.1:5984/_replicator
curl -X PUT http://admin:1qaz2wsx@127.0.0.1:5984/_global_changes
```

## 2. Setup Log

### ເຂົ້າໄປໃນ folder log ແລ້ວ Run command

```
docker-compose up -d
```

## 3. Setup Storage

### ເຂົ້າໄປໃນ folder storage ແລ້ວແກ້ໄຂ file nginx.conf
1. ແຖວທີ່ 37 ໃຫ້ເປັນ domain ທີ່ຕ້ອງການ
2. ແຖວທີ່ 48 ໃຫ້ເປັນ fullchain
3. ແຖວທີ່ 49 ໃຫ້ເປັນ private key


### ແລ້ວ Run command

```
docker-compose up -d
```

## 4. Setup Redis & Postgres

### ເຂົ້າໄປໃນ folder env ແລ້ວ Run command

```
docker-compose up -d
```

## 5. Setup App

### ເຂົ້າໄປໃນ folder app ແລ້ວ Run command

ເຂົ້າໄປແປງ IP ໃຫ້ຖືກຕ້ອງ

```
docker-compose up -d
```

## 6. Setup Load Balance

### ເຂົ້າໄປໃນ folder haproxy
 ແລ້ວ Run command

ເຂົ້າໄປເອົາ file haproxy.cfg ແລະ eoffice_la.pem ໄປໄວ້ບ່ອນທີ່ກຳໜົດ

ສຳລັບ ແມ່ນໃຫ້ແກ້ໄຂ IP ກ່ອນ haproxy.cfg
```
/etc/haproxy/haproxy.cfg
```
ສຳລັບ eoffice_la.pem
```
/opt/eoffice_la.pem
```
ແລ້ວສັ່ງ command
```
sudo systemctl restart haproxy
```
