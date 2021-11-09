## How To Goon Auth
Use the following steps to setup your own goon auth network system.

### Clone the projects
```
git clone ...
```

### Configure project paths
Change paths inside `workspace.code-workspace`
Change paths inside `docker-compose.yaml` under the following services:
- `awful-auth`
- `goon-files`
- `discord-auth`

### Configure environment variables
```
cp .env.example .env
nano .env
```

### Create persistent volumes
```
docker volume create --name mongo_data
docker volume create --name redis_data
```

### Run it!
```
docker-compose up -d
```

## Discord Setup

### New Application
Create a new application for your bot on [discord's developer portal](https://discord.com/developers/applications).

Be sure to create a bot user for the application. This is required to manage permissions on a server.

### Pull Application Settings
Use the following settings found under your discord application's setting page in `.env`

| Application (Setting Page) | .env key                | Used for                          |
| -------------------------- | ----------------------- | --------------------------------- |
| APPLICATION ID (General)   | DISCORD_APPLICATION_ID  | Creating commands                 |
| PUBLIC KEY (General)       | DISCORD_PUBLIC_KEY      | Verifying incoming commands       |
| TOKEN (Bot)                | DISCORD_BOT_TOKEN       | Creating commands, managing roles |

### Configure Interaction Endpoint
For discord to push commands you need to configure the endpoint under the application's setting page.

Under `General Information` set the `Interactions Endpoint Url` to `https://YOUR_SERVER_NAME/interactions`. By default the docker compose file exposes discord-auth on port 8080 and will require SSL termination and forwarding to 8080.