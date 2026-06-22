# Docker PostgreSQL + Adminer

Setup sederhana PostgreSQL dan Adminer menggunakan Docker Compose.

## Services

| Service | Port | Description |
|----------|----------|----------|
| PostgreSQL | 5432 | Database PostgreSQL |
| Adminer | 8080 | Database Management UI |

## Structure

```text
docker-postgres-adminer/
├── README.md
└── docker-compose.yml
```

## Run

Menjalankan container:

```bash
docker compose up -d
```

Melihat status:

```bash
docker ps
```

Melihat log:

```bash
docker compose logs -f
```

Stop container:

```bash
docker compose down
```

Stop dan hapus volume:

```bash
docker compose down -v
```

## PostgreSQL Credentials

| Key | Value |
|------|------|
| Host | postgres |
| Port | 5432 |
| Database | app_db |
| Username | postgres |
| Password | postgres |

## Access Adminer

Buka browser:

```text
http://localhost:8080
```

Login menggunakan:

```text
System: PostgreSQL
Server: postgres
Username: postgres
Password: postgres
Database: app_db
```

## Connect From Local Machine

Gunakan:

```env
DB_CONNECTION=pgsql
DB_HOST=localhost
DB_PORT=5432
DB_DATABASE=app_db
DB_USERNAME=postgres
DB_PASSWORD=postgres
```

## Persistent Storage

Data PostgreSQL disimpan pada Docker Volume:

```text
postgres_data
```

Sehingga data tidak hilang saat container restart.

## Upgrade PostgreSQL Version

Edit image pada docker-compose.yml:

```yaml
image: postgres:17
```

Kemudian:

```bash
docker compose pull
docker compose up -d
```
