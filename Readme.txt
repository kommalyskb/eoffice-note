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
docker build -t codecamplao/eoffice-frontend:v3.8.0.3 -f .\GOffice.Frontend\Dockerfile .
docker build -t codecamplao/eoffice-api:v3.8.0.3 -f .\GOffice.APIGateway\Dockerfile .
docker build -t codecamplao/eoffice-webjob:v1.0.0 -f .\WebJobAPI\Dockerfile .

#Run docker
docker run --rm -d codecamplao/eoffice-frontend:v3.8.0.3
docker run --rm -d codecamplao/eoffice-api:v3.8.0.3
docker run --rm -d codecamplao/eoffice-webjob:v1.0.0
