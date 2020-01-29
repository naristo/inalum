# elastic-docker-compose

## run `docker-compose -f elastic-docker.yml up`
---

Run this after es-01 up 
`docker exec es-01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url http://es-01:9200"`
and update kibana password in elastic-docker.yml 
