# Deploy elastic-stack using docker-compose


## Requirement
* VM Machine ( virtualbox + vagrant )
* Docker
* Docker Compose

Untuk menggunakan repo ini : 
* install docker 
```
curl -fsSL https://get.docker.com -o get-docker.sh
chmod a+x get-docker.sh
./get-docker.sh
```
* install docker-compose 
```
curl -L https://github.com/docker/compose/releases/download/1.25.3/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
cp /usr/local/bin/docker-compose /usr/sbin
```
* clone repo aris
`git clone http://gitlab.digi.corp.bankbtpn.co.id/naristo/elastic-docker-compose.git`

```
Opsi : Bagi yang biasa menggunakan Vagrant jalankan `vagrant up` dilanjut deploy elastic stack 
       run `vagrant ssh` untuk ssh ke virtual machine yang sudah di create menggunakan vagrant
sysctl -w vm.max_map_count=262144

```
## Untuk deploy Elastic Stack tanpa mengaktifkan Auth jalankan 
run `docker-compose -f script/elastic-docker.yml up`



---
## Untuk deploy Elastic Stack dengan Auth jalankan
run `docker-compose -f script/elastic-docker-auth.yml up`

setelah docker es-01 up & running lanjutkan dengan setup password untuk elasticsearch
* buka terminal baru 
* jalankan command `docker exec es-01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url http://es-01:9200"`
* copy user dan password yang tergenerate di screen `simpan atau di hapalkan`
dan update kibana password in elastic-docker-auth.yml

--- 


