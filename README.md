# prisma-postgresql-example
Prisma with PostgreSQL example

Prerequisites
- Docker

### Install the Prisma CLI
```
npm install -g prisma
```

### Start database and Prisma server
```
cd server
docker-compose up -d
```

### Configure your Prisma API
```
prisma init --endpoint http://localhost:4466
```

### Generate your Prisma client
> At project root
```
echo "
generate:
  - generator: javascript-client
    output: ./prisma-client/" >> prisma.yml
```

### Prepare Node application
```
npm init -y
npm install --save prisma-client-lib graphql
```

