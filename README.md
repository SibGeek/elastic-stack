cd %elastic-stack_docker-compose_project_folder%

docker-compose up -d

docker exec -it elasticsearch-service-container bash

./usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive

#Interactive password setting for built-in ElasticSearch accounts

exit

docker exec -it kibana-service-container bash

./usr/share/kibana/bin/kibana-keystore create

./usr/share/kibana/bin/kibana-keystore add elasticsearch.password

#Entering the built-in ElasticSearch account "kibana_system" password from previous step

exit

docker-compose restart

#Open browser at the URL http://%kibana-container-ip%:5601
