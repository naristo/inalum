# Inalum elastic-stack using docker-compose

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
`git clone https://github.com/naristo/inalum.git`

* update config dari git
```
cd inalum
git pull
```

```
sysctl -w vm.max_map_count=262144
vim /etc/sysctl.conf
tambahkan vm.max_map_count=262144
```
## Untuk deploy Elastic Stack tanpa mengaktifkan Auth jalankan 
run `docker-compose -f script/elastic-docker.yml up`



---
## Untuk deploy Elastic Stack dengan Auth jalankan
run `docker-compose -f script/elastic-docker-auth.yml up`

setelah docker es-master-01 up & running lanjutkan dengan setup password untuk elasticsearch
* buka terminal baru 
* jalankan command `docker exec es-master-01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url http://es-master-01:9200"`
* copy user dan password yang tergenerate di screen `simpan atau di hapalkan`
dan update kibana password in elastic-docker-auth.yml

--- 
## Usage
* untuk restart salah satu instance : `docker-compose -f elastic-docker-auth.yml restart [nama-instance]`
* untuk apply update config : `docker-compose -f elastic-docker-auth.yml pull`

