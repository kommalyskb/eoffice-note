#Front-end
domain: https://uat.eoffice.la
202.137.50.53

#Api 
domain: https://uat-api.eoffice.la
202.137.50.53

#WebJob
domain: https://job-uat.eoffice.la
202.137.50.53

#Database couchdb
domain: db.local
ip: 10.1.1.74
port: 5984

#Database Postgress
domain: postgres.local
ip: 10.1.1.75
port: 5432

#Redis
domain: redis.local
ip: 10.1.1.70
port: 6379

#Kafka
domain: lb02.eofficev3
ip: 10.1.1.71
port: 9092

#Elastic
domain: http://log.local
ip: 10.1.1.70
port: 9200

#Repository
codecamplao/eoffice-frontend
codecamplao/eoffice-api
codecamplao/eoffice-webjob

#Build docker profile
---------------UAT
docker build -t codecamplao/eoffice-frontend:v3.8.1.4a -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4a -f .\GOffice.APIGateway\Dockerfile .
---------------MTC
docker build -t codecamplao/eoffice-frontend:v3.8.1.4a-mtc -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4a-mtc -f .\GOffice.APIGateway\Dockerfile .
---------------NA
docker build -t codecamplao/eoffice-frontend:v3.8.1.4a-na -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4a-na -f .\GOffice.APIGateway\Dockerfile .
---------------MON
docker build -t codecamplao/eoffice-frontend:v3.8.1.4a-monre -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4a-monre -f .\GOffice.APIGateway\Dockerfile .
---------------MOHA
docker build -t codecamplao/eoffice-frontend:v3.8.1.4c-moha -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4d-moha -f .\GOffice.APIGateway\Dockerfile .
---------------VTE
docker build -t codecamplao/eoffice-frontend:v3.8.1.4a-vte -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.1.4a-vte -f .\GOffice.APIGateway\Dockerfile .
--------------MigrantStorage
docker build -t codecamplao/eoffice-migrant-storage:v1.0.5 .
--------------Cloud signing Web
docker build -t codecamplao/cloud-signing-web:v1.0.7 -f .\eOffice.CloudSigning\Dockerfile .


docker build -t codecamplao/eoffice-hub:v1.0.3 -f .\GOffice.Hub\Dockerfile .

docker build -t codecamplao/eoffice-webjob:v1.0.6 -f .\WebJobAPI\Dockerfile .

#Run docker
docker run --rm -d codecamplao/eoffice-frontend:v3.8.1.1d
docker run --rm -d codecamplao/eoffice-api:v3.8.1.1f
docker run --rm -d codecamplao/eoffice-webjob:v1.0.0
docker run --rm -d codecamplao/eoffice-hub:v1.0.3

#Push
---------------UAT
docker push codecamplao/eoffice-frontend:v3.8.1.4a
docker push codecamplao/eoffice-api:v3.8.1.4a
docker push codecamplao/eoffice-hub:v1.0.3
docker push codecamplao/eoffice-webjob:v1.0.6
---------------MTC
docker push codecamplao/eoffice-frontend:v3.8.1.4a-mtc
docker push codecamplao/eoffice-api:v3.8.1.4a-mtc
---------------NA
docker push codecamplao/eoffice-frontend:v3.8.1.4a-na
docker push codecamplao/eoffice-api:v3.8.1.4a-na
---------------MONRE
docker push codecamplao/eoffice-frontend:v3.8.1.4a-monre
docker push codecamplao/eoffice-api:v3.8.1.4a-monre
---------------MOHA
docker push codecamplao/eoffice-frontend:v3.8.1.4c-moha
docker push codecamplao/eoffice-api:v3.8.1.4d-moha
---------------VTE
docker push codecamplao/eoffice-frontend:v3.8.1.4a-vte
docker push codecamplao/eoffice-api:v3.8.1.4a-vte
--------------MigrantStorage
docker push codecamplao/eoffice-migrant-storage:v1.0.5
--------------Cloud signing Web
docker push codecamplao/cloud-signing-web:v1.0.7
