# learn-ecs-backend

Backend API for ECS three-tier demo.

## Local Test

```bash
docker compose up --build
```

Backend URL:

```text
http://localhost:8000
```

Health check:

```bash
curl http://localhost:8000/api/health
```

## Backend API

```text
GET    /api/health
GET    /api/stats
GET    /api/users
POST   /api/register
DELETE /api/users/:id
```

## ECS Task Definition

Task definition family:

```text
learn-ecs-backend
```

Container name:

```text
learn-ecs-backend
```

Container port:

```text
8000
```

## ECS Environment Variables

```text
FLASK_ENV=production
DB_HOST=learn-ecs-db
DB_PORT=5432
POSTGRES_DB=learn_devops
POSTGRES_USER=learn_user
POSTGRES_PASSWORD=learn_password
```

If you use Cloud Map namespace like `ecs.local`, use:

```text
DB_HOST=learn-ecs-db.ecs.local
```

## Security Group

Backend inbound:

```text
Port 8000
Source = frontend security group or internal ALB security group
```

Backend outbound:

```text
Allow 5432 to db security group
```
