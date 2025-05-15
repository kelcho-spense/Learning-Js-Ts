# Generics-Practise Scenarios

1. Create a **generic interface** for our database operations.
2. Create a **generic class** that implements the interface.
3. Use **generics to define flexible methods** that can handle different types of data.

### Step 1: Define a `DatabaseEntity` interface

The first step is to define an interface that represents a generic database entity. This interface will enforce that all entities in our mock database will at least have an `id`.

```typescript
interface DatabaseEntity {
  id: string;
}

```

Here, `DatabaseEntity` is a very basic interface. Every database entity will have an `id` property that is a string.

### Step 2: Define a `Database` class that uses generics

Now, we will create a class `Database` that works with a generic type. This class will contain methods like `create`, `read`, `update`, and `delete`. The idea is to make this class flexible enough to handle any type of data, not just a fixed shape.

```typescript
class Database<T extends DatabaseEntity> {
  private data: T[] = [];  // Holds the data for our mock DB

  // Create a new entity
  create(entity: T): void {
    this.data.push(entity);
  }

  // Read a specific entity by its ID
  read(id: string): T | undefined {
    return this.data.find(entity => entity.id === id);
  }

  // Update an existing entity
  update(id: string, updatedEntity: T): boolean {
    const index = this.data.findIndex(entity => entity.id === id);
    if (index !== -1) {
      this.data[index] = updatedEntity;
      return true;
    }
    return false;
  }

  // Delete an entity by its ID
  delete(id: string): boolean {
    const index = this.data.findIndex(entity => entity.id === id);
    if (index !== -1) {
      this.data.splice(index, 1);
      return true;
    }
    return false;
  }
}
```

### Explanation of the Code:

1. **`T extends DatabaseEntity`**: This ensures that `T` is a type that extends `DatabaseEntity`. In simpler terms, it ensures that `T` always has at least the `id` property, which is necessary for any operation on the database.
2. **`data: T[]`**: This is our dummy database that holds an array of `T` objects (generic objects that extend `DatabaseEntity`).
3. **CRUD Methods**:

    * `create(entity: T)`: Adds a new entity to the database.
    * `read(id: string)`: Finds and returns an entity by `id`.
    * `update(id: string, updatedEntity: T)`: Updates an existing entity in the database.
    * `delete(id: string)`: Removes an entity by `id`.

The class `Database<T>` is **generic**, meaning it can work with any type `T` that satisfies the `DatabaseEntity` interface.

### Step 3: Create Specific Types (Entities)

Now, let's create some concrete entity types that will be used with our generic `Database` class.

#### Example 1: `User` Entity

```typescript
interface User extends DatabaseEntity {
  name: string;
  email: string;
}

const userDB = new Database<User>();

// Adding a user
userDB.create({ id: '1', name: 'Alice', email: 'alice@example.com' });
userDB.create({ id: '2', name: 'Bob', email: 'bob@example.com' });

// Reading a user
const user = userDB.read('1');
console.log(user);  // Output: { id: '1', name: 'Alice', email: 'alice@example.com' }

// Updating a user
const updateSuccess = userDB.update('1', { id: '1', name: 'Alice Cooper', email: 'alicecooper@example.com' });
console.log(updateSuccess);  // Output: true

// Deleting a user
const deleteSuccess = userDB.delete('2');
console.log(deleteSuccess);  // Output: true
```

#### Example 2: `Product` Entity

```typescript
interface Product extends DatabaseEntity {
  name: string;
  price: number;
}

const productDB = new Database<Product>();

// Adding a product
productDB.create({ id: '101', name: 'Laptop', price: 999.99 });
productDB.create({ id: '102', name: 'Smartphone', price: 699.99 });

// Reading a product
const product = productDB.read('101');
console.log(product);  // Output: { id: '101', name: 'Laptop', price: 999.99 }

// Updating a product
const productUpdateSuccess = productDB.update('101', { id: '101', name: 'Laptop Pro', price: 1199.99 });
console.log(productUpdateSuccess);  // Output: true

// Deleting a product
const productDeleteSuccess = productDB.delete('102');
console.log(productDeleteSuccess);  // Output: true
```

### Step 4: Key Concepts of Generics in Action

1. **Flexibility**: The `Database` class can handle different types of entities (e.g., `User`, `Product`) without rewriting code for each one.
2. **Type Safety**: We ensure that `T` will always be a valid type (it must extend `DatabaseEntity`), which means TypeScript will give us errors at compile time if we try to use an incorrect structure.
3. **Code Reusability**: The `Database` class can be reused with any type that extends `DatabaseEntity`, reducing boilerplate code and increasing maintainability.

### Step 5: Why Use Generics?

* **Type Safety**: Ensures that operations like `.create()`, `.read()`, `.update()`, and `.delete()` are type-safe and don't accept or return incorrect data.
* **Reusability**: We don’t need to write a separate class for each type of entity (e.g., one class for users, one for products). We only write the generic class once and use it for all types.
* **Extendability**: If you want to add more entity types in the future (e.g., `Order`, `Invoice`), you just define a new interface and pass it to the `Database` class.

---

### Recap:

* **Generics** allow you to write **flexible, reusable, and type-safe code** that can handle a variety of data types without duplicating logic.
* We created a generic `Database<T>` class that can be used with any entity that extends `DatabaseEntity`.
* By using generics, we avoid hard-coding types, making the class reusable and type-safe across different entities (`User`, `Product`, etc.).
