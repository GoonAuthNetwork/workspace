## How To Goon Auth
Use the following steps to setup your own goon auth network system.

### Clone the projects
```
git clone ...
```

### Configure project paths
Change paths inside `workspace.code-workspace`
Change paths inside `docker-compse.yaml` under the following services:
- `awful-auth`
- `goon-files`
- `discord-auth`

### Configure environment variables
```
cp .env.example .env
nano .env
```

### Create persistance volumes
```
docker volume create --name mongo_data
docker volume create --name redis_data
```

### Run it!
```
docker-compose up -d
```