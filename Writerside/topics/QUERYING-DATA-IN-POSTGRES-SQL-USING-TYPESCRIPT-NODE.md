# QUERYING DATA IN POSTGRES SQL USING TYPESCRIPT &amp; NODE

## [node-postgres](https://node-postgres.com/)

node-postgres is a collection of node.js modules for interfacing with your PostgreSQL database. It has support for callbacks, promises, async/await, connection pooling, prepared statements, cursors, streaming results, C/C++ bindings, rich type parsing, and more! Just like PostgreSQL itself there are a lot of features: this documentation aims to get you up and running quickly and in the right direction

### Pooling

In most applications you'll wannt to use a [connection pool](https://node-postgres.com/features/pooling) to manage your connections.

```typescript
import { Pool } from 'pg'
const pool = new Pool()
const res = await pool.query('SELECT $1::text as message', ['Hello world!'])
console.log(res.rows[0].message) // Hello world!
```

#### Why pooling ?

* Connecting a new client to the PostgreSQL server requires a handshake which can take 20-30 milliseconds. During this time passwords are negotiated, SSL may be established, and configuration information is shared with the client & server. Incurring this cost *every time* we want to execute a query would substantially slow down our application.
* The PostgreSQL server can only handle a [limited number of clients at a time](https://wiki.postgresql.org/wiki/Number_Of_Database_Connections). Depending on the available memory of your PostgreSQL server you may even crash the server if you connect an unbounded number of clients.
* The PostgreSQL server can only handle a [limited number of clients at a time](https://wiki.postgresql.org/wiki/Number_Of_Database_Connections). Depending on the available memory of your PostgreSQL server you may even crash the server if you connect an unbounded number of clients.

### Single Query

If you don't need a transaction or you just need to run a single query, the pool has a convenience method to run a query on any available client in the pool. This is the preferred way to query with node-postgres if you can as it removes the risk of leaking a client.

```typescript
import pg from 'pg'
const { Pool } = pg
 
const pool = new Pool()
 
const res = await pool.query('SELECT * FROM users WHERE id = $1', [1])
console.log('user:', res.rows[0])
```

### Parameterized query

If you are passing parameters to your queries you will want to avoid string concatenating parameters into the query text directly. This can (and often does) lead to sql injection vulnerabilities. node-postgres supports parameterized queries, passing your query text *unaltered* as well as your parameters to the PostgreSQL server where the parameters are safely substituted into the query with battle-tested parameter substitution code within the server itself.

```typescript
const text = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *'
const values = ['brianc', 'brian.m.carlson@gmail.com']
 
const res = await pool.query(text, values)
console.log(res.rows[0])
// { name: 'brianc', email: 'brian.m.carlson@gmail.com' }
```

### Query Config Object

`pool.query` and `client.query` both support taking a config object as an argument instead of taking a string and optional array of parameters. The same example above could also be performed like so:

```typescript
const query = {
  text: 'INSERT INTO users(name, email) VALUES($1, $2)',
  values: ['brianc', 'brian.m.carlson@gmail.com'],
}
 
const res = await client.query(query)
console.log(res.rows[0])
```

The query config object allows for a few more advanced scenarios:

PostgreSQL has the concept of a [prepared statement](https://www.postgresql.org/docs/9.3/static/sql-prepare.html). node-postgres supports this by supplying a `name` parameter to the query config object. If you supply a `name` parameter the query execution plan will be cached on the PostgreSQL server on a  **per connection basis** . This means if you use two different connections each will have to parse & plan the query once. node-postgres handles this transparently for you: a client only requests a query to be parsed the first time that particular client has seen that query name:

```typescript
const query = {
  // give the query a unique name
  name: 'fetch-user',
  text: 'SELECT * FROM user WHERE id = $1',
  values: [1],
}
 
const res = await client.query(query)
console.log(res.rows[0])
```

### Prepared statements

PostgreSQL has the concept of a [prepared statement](https://www.postgresql.org/docs/9.3/static/sql-prepare.html). node-postgres supports this by supplying a `name` parameter to the query config object. If you supply a `name` parameter the query execution plan will be cached on the PostgreSQL server on a  **per connection basis** . This means if you use two different connections each will have to parse & plan the query once. node-postgres handles this transparently for you: a client only requests a query to be parsed the first time that particular client has seen that query name:

```typescript
const query = {
  // give the query a unique name
  name: 'fetch-user',
  text: 'SELECT * FROM user WHERE id = $1',
  values: [1],
}
 
const res = await client.query(query)
console.log(res.rows[0])
```

### Transactions

```typescript
import { Pool } from 'pg'
const pool = new Pool()
 
const client = await pool.connect()
 
try {
  await client.query('BEGIN')
  const queryText = 'INSERT INTO users(name) VALUES($1) RETURNING id'
  const res = await client.query(queryText, ['brianc'])
 
  const insertPhotoText = 'INSERT INTO photos(user_id, photo_url) VALUES ($1, $2)'
  const insertPhotoValues = [res.rows[0].id, 's3.bucket.foo']
  await client.query(insertPhotoText, insertPhotoValues)
  await client.query('COMMIT')
} catch (e) {
  await client.query('ROLLBACK')
  throw e
} finally {
  client.release()
}
```

## Getting Started (Project Setup)

### Prerequisites

- Node.js (v22 or later)
- pnpm (or npm)
- PostgreSQL installed and running or in a Docker container

### Installation Steps

1. Clone the repository (or create a new directory):

   ```bash
   mkdir ts-node-postgres
   cd ts-node-postgres
   ```
2. Initialize the project:

   ```bash
   pnpm init
   ```
3. Install required dependencies:

   ```bash
   # Core dependencies
   pnpm add pg dotenv

   # Development dependencies
   pnpm add -D @types/node @types/pg tsx typescript
   ```
4. Initialize TypeScript configuration if not already present:

   ```bash
   npx tsc --init
   ```

   and add below ts config

   ```json
   {
     "compilerOptions": {
       "target": "ES2024", /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */
       "module": "NodeNext", /* Specify what module code is generated. */
       "rootDir": "./src", /* Allow multiple folders to be treated as one when resolving modules. */
       "outDir": "./dist", /* Specify an output folder for all emitted files. */
       "esModuleInterop": true, /* Emit additional JavaScript to ease support for importing CommonJS modules. This enables 'allowSyntheticDefaultImports' for type compatibility. */
       "forceConsistentCasingInFileNames": true, /* Ensure that casing is correct in imports. */
       "strict": true, /* Enable all strict type-checking options. */
       "skipLibCheck": true, /* Skip type checking all .d.ts files. */
       "resolveJsonModule": true,
     },
     "include": [
       "src/**/*.ts", // Include all .ts files
     ],
     "exclude": [
       "node_modules" // Exclude node_modules from the compilation process
     ]
   }
   ```
5. Create project structure:

   ```
   ts-node-postgres/
   ├── src/
   │   ├── config
   │   │	└── database.ts
   │   │	└── env.ts
   │   └── examples/
   │       └── basic-query.ts
   │   └── index.ts
   ├── .env
   ├── .gitignore
   ├── package.json
   └── tsconfig.json
   ```
6. Setup environment variables (create `.env` file):

   ```
   # PostgreSQL Connection
   PGHOST=localhost
   PGUSER=postgres
   PGDATABASE=your_database
   PGPASSWORD=your_password
   PGPORT=5432

   ```
7. Create a `.gitignore` file to exclude sensitive information:

   ```
   node_modules/
   dist/
   .env
   .env.*
   !.env.example
   ```

## Environment Setup

### Loading Environment Variables

Create a utility file to load environment variables:

```typescript
// src/config/env.ts
import dotenv from 'dotenv';
import path from 'path';

// Load environment variables from .env file
const result = dotenv.config({
  path: path.resolve(process.cwd(), '.env')
});

if (result.error) {
  console.error('Error loading .env file:', result.error);
}

export default {
  database: {
    host: process.env.PGHOST || 'localhost',
    port: parseInt(process.env.PGPORT || '5432', 10),
    user: process.env.PGUSER || 'postgres',
    password: process.env.PGPASSWORD || '',
    database: process.env.PGDATABASE || 'postgres',
  }
};

```

### Database Configuration File

Use the environment config in your database setup:

```typescript
// src/config/database.ts
import env from './env'
import { Pool, PoolConfig, QueryResult } from 'pg'

class Database {
    private pool: Pool;
  
    constructor() {
        const poolConfig: PoolConfig = {
            host: env.database.host,
            port: env.database.port,
            user: env.database.user,
            password: env.database.password,
            database: env.database.database,
            max: 20,
            idleTimeoutMillis: 30000,
            connectionTimeoutMillis: 5000,
            // For production with SSL:
            // ssl: {
            //   rejectUnauthorized: false
            // }
        };
  
        this.pool = new Pool(poolConfig);
  
        this.pool.on('connect', () => {
            console.log('Connected to PostgreSQL database');
        });
  
        this.pool.on('error', (err) => {
            console.error('Unexpected error on idle client', err);
            process.exit(-1);
        });
    }
  
    async executeQuery(text: string, params: any[] = []): Promise<QueryResult> {
        const client = await this.pool.connect();
        try {
            const start = Date.now();
            const result = await client.query(text, params);
            const duration = Date.now() - start;
            console.log(`Executed query: ${text} - Duration: ${duration}ms`);
            return result;
        } catch (error) {
            console.error('Database query error:', error);
            throw error;
        } finally {
            client.release();
        }
    }
  
    async initializeTables(): Promise<void> {
        try {
            // create users table
            await this.executeQuery(`
                CREATE TABLE IF NOT EXISTS users (
                    id SERIAL PRIMARY KEY,
                    fname VARCHAR(50) NOT NULL,
                    lname VARCHAR(50) NOT NULL,
                    age INT,
                    created_at TIMESTAMPTZ DEFAULT NOW()
                )
            `);
            console.log('Users table created or already exists');

            // create other tables as needed
            console.log('Database schema initialized successfully');
        } catch (err) {
            console.error('Error initializing database:', err);
            throw err;
        }
    }
  
    getPool(): Pool {
        return this.pool;
    }
}

// Create singleton instance
const db = new Database();

// Export instance methods and the database object
export const executeQuery = (text: string, params: any[] = []) => db.executeQuery(text, params);
export const initializeTables = () => db.initializeTables();
export default db;

```

## Using the Database

### Basic Query

```typescript
import db, { executeQuery } from "../config/database";

// User interface defining the structure of user data
export interface TUser {
    id?: number;
    fname: string;
    lname: string;
    age: number;
    created_at?: Date;
}

// Insert a single user into the database
export const insertOneUser = async (user: TUser): Promise<number | undefined> => {
    try {
        const res = await executeQuery(
            'INSERT INTO users (fname, lname, age) VALUES ($1, $2, $3) RETURNING id',
            [user.fname, user.lname, user.age]
        );
        const userId = res.rows[0]?.id;
        console.log(`User inserted with ID: ${userId}`);
        return userId;
    } catch (err) {
        console.error('Error inserting data:', err);
        throw err;
    }
}


// Insert multiple users into the database
export const insertMultipleUsers = async (users: TUser[]): Promise<void> => {
    // For multiple users, using a transaction is better
    const client = await db.getPool().connect();
    try {
        // Begin transaction
        await client.query('BEGIN');

        // Insert each user
        for (const user of users) {
            await client.query(
                'INSERT INTO users (fname, lname, age) VALUES ($1, $2, $3)',
                [user.fname, user.lname, user.age]
            );
        }

        // Commit transaction
        await client.query('COMMIT');
        console.log(`${users.length} users inserted successfully`);
    } catch (err) {
        await client.query('ROLLBACK');
        console.error('Error inserting multiple users:', err);
        throw err;
    } finally {
        client.release();
    }
}

// Query all users from the database
export const query = async (): Promise<TUser[]> => {
    try {
        const res = await executeQuery('SELECT * FROM users');
        console.log(`Retrieved ${res.rows.length} users`);
        return res.rows as TUser[];
    } catch (err) {
        console.error('Error querying data:', err);
        throw err;
    }
};

// delete all users from the database
export const deleteAllUsers = async (): Promise<void> => {
    try {
        const res = await executeQuery('DELETE FROM users');
        console.log(`Deleted ${res.rowCount} users`);
    } catch (err) {
        console.error('Error deleting data:', err);
        throw err;
    }
}
```

## Executing Queries in Index.ts

```typescript
import { initializeTables } from './config/database';
import { query, insertMultipleUsers, insertOneUser, TUser, deleteAllUsers } from './examples/basic-query'

// Self-executing async function to run the imported code
(async () => {
    try {
        // user operations

        // 1. Create tables if it doesn't exist
        await initializeTables();

        // 2. Insert a test user
        const userId = await insertOneUser({ fname: 'John', lname: 'Doe', age: 30 });
        console.log(`Inserted user with ID: ${userId}`);

        // 3. Insert multiple users with a transaction
        const usersToInsert: TUser[] = [
            { fname: 'Jane', lname: 'Smith', age: 28 },
            { fname: 'Bob', lname: 'Johnson', age: 35 },
        ];
        await insertMultipleUsers(usersToInsert);

        // 4. Query all users to verify
        const users = await query();
        console.log('All users in database:');
        console.table(users);
        // 5. Delete all users
        // await deleteAllUsers();

        console.log('All operations completed successfully');
    } catch (error) {
        console.error('Error executing database operations:', error);
    }
})();
```