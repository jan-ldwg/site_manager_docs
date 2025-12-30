# Installation

site_manager is available on [ghcr.io](https://github.com/users/jan-ldwg/packages/container/package/site_manager_server) as a prebuilt container image for arm64 and x84/amd64. This tutorial will show you how to pull the image from ghcr.io and deploy it together with a PostgreSQL database using Docker Desktop.

### 1. Install Docker Desktop

Docker Desktop is available [here](https://www.docker.com/products/docker-desktop/) for all major platforms.

### 2. Set up environment variables

Open an empty folder in an editor of your choice (this tutorial uses [VSCode](https://code.visualstudio.com/)). Create a file called `.env`. In this file, you will set up basic parameters and names for the application and the database. Be sure to set at least a `POSTGRES_USER`, `POSTGRES_PASSWORD`, the corresponding `DATABASE_URL` and a `BETTER_AUTH_SECRET`. You can generate a secret [here](https://www.better-auth.com/docs/installation#set-environment-variables).

```title=".env"
POSTGRES_DB="site-manager-db"
POSTGRES_USER="<your username>"
POSTGRES_PASSWORD="<your password>"

DATABASE_URL="postgres://<your username>:<your password>@db:5432/site-manager-db"

PORT=5056

BETTER_AUTH_SECRET= "superlongstring"
#secret for Better Auth, 32 character base64 string,
#see https://www.better-auth.com/docs/installation#set-environment-variables
BETTER_AUTH_URL=http://localhost:5056 # Base URL of the app

DEFAULT_ADMIN_USER="admin"
DEFAULT_ADMIN_PASSWORD="password"
DEFAULT_ADMIN_EMAIL="admin@example.com" #this is only for login, site_manager will not send you any email.

```

### 3. Configure compose.yaml

In the same folder, create a file called `compose.yaml`.

```yaml title="compose.yaml"
services:
  server:
    image: ghcr.io/jan-ldwg/site_manager_server:latest
    container_name: site-manager-server
    environment:
      NODE_ENV: production
      DATABASE_URL: ${DATABASE_URL}
      PORT: ${PORT}
      BETTER_AUTH_SECRET: ${BETTER_AUTH_SECRET}
      BETTER_AUTH_URL: ${BETTER_AUTH_URL}
      DEFAULT_ADMIN_USER: ${DEFAULT_ADMIN_USER}
      DEFAULT_ADMIN_PASSWORD: ${DEFAULT_ADMIN_PASSWORD}
      DEFAULT_ADMIN_EMAIL: ${DEFAULT_ADMIN_EMAIL}
    ports:
      - 5056:5056
    depends_on:
      db:
        condition: service_healthy
    restart: unless-stopped
    tmpfs:
      - /tmp
    networks:
      - site-manager-network

  db:
    image: postgres:14.20-alpine3.23
    container_name: site-manager-db
    restart: always
    environment:
      POSTGRES_DB: "${POSTGRES_DB}"
      POSTGRES_USER: "${POSTGRES_USER}"
      POSTGRES_PASSWORD: "${POSTGRES_PASSWORD}"

    volumes:
      - db-data:/var/lib/postgresql/data

    expose:
      - 5432
    healthcheck:
      test:
        [
          "CMD",
          "pg_isready",
          "--username=${POSTGRES_USER}",
          "--dbname=${POSTGRES_DB}",
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 5s
    networks:
      - site-manager-network
volumes:
  db-data:

networks:
  site-manager-network:
    name: site-manager-network
    driver: bridge
```

### 4. Run in Docker Desktop

Open a terminal in your working directory and run

```sh
docker compose up -d
```

Docker should automatically fetch the required images and set up an empty database

### 5. Login

Go to [http://localhost:5056](http://localhost:5056) and login with the account you set up in your `.env`. This account has admin privileges and can be used to add additional user accounts.
