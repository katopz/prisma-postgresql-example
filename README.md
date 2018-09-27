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

### Read and write data using the Prisma client
```js
const { prisma } = require('./prisma-client')

// A `main` function so that we can use async/await
async function main() {

  // Create a new user called `Alice`
  const newUser = await prisma.createUser({ name: 'Alice' })
  console.log(`Created new user: ${newUser.name} (ID: ${newUser.id})`)

  // Read all users from the database and print them to the console
  const allUsers = await prisma.users()
  console.log(allUsers)
}

main().catch(e => console.error(e))
```
and run
```
node index
```