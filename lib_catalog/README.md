### Docker commands for homework lesson 2

# Create network for backend and DB:
`docker network create --subnet 192.168.8.0/24 --gateway=192.168.8.1 --ip-range 192.168.8.0/24 --label=backend_net backend_net`

# Build and Up container for backend:
```
docker build -t my-backend-2 .
docker run -d -p 8000:8000 --name my-backend-2 --net backend_net --ip=192.168.8.100 my-backend-2
```

# Database postgresql command run container:
```
docker run -d -p 5432:5432 --name postgresql_db --net backend_net --ip=192.168.8.101 -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django  -e POSTGRES_NAME=django postgres:alpine3.14
```
