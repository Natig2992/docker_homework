### Docker commands for homework lesson 2

# Create network for backend and DB:
`docker network create --subnet 192.168.8.0/24 --gateway=192.168.8.1 --ip-range 192.168.8.0/24 --label=backend_net backend_net`

# Build and Up container for backend:
```
docker build -t my_backend:v1.0 -t my_backend:latest .
docker run -d -p 8000:8000 --name backend-app --net backend_net --ip=192.168.8.100 my_backend:v1.0
```

# Database postgresql command run container:
```
docker run -d --name postgres_db --net backend_net --ip=192.168.8.101 -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django  -e POSTGRES_NAME=django postgres:13
```
# Change DB connectivity in setting.py file:

```
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "django",
        "USER": "django",
        "PASSWORD": "django",
        "HOST": "postgres_db",
        "PORT": "5432",
        "CONN_MAX_AGE": None
    },
}
```
