# DOM: Movie Project & IndexedDB

## Movie Management System with TypeScript and IndexedDB

This project demonstrates how to build a Movie Management System using TypeScript and the browser's native IndexedDB for persistent storage. The application allows users to add, edit, delete, and rate movies.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Project Setup](#project-setup)
- [Step-by-Step Guide](#step-by-step-guide)
    - [Step 1: Setting up the Project Structure](#step-1-setting-up-the-project-structure)
    - [Step 2: Creating the Movie Interface](#step-2-creating-the-movie-interface)
    - [Step 3: Building the Database Service](#step-3-building-the-database-service)
    - [Step 4: Setting up the UI](#step-4-setting-up-the-ui)
    - [Step 5: Implementing CRUD Operations](#step-5-implementing-crud-operations)
    - [Step 6: Styling the Application](#step-6-styling-the-application)
- [Running the Application](#running-the-application)
- [Key Learning Points](#key-learning-points)
- [Next Steps](#next-steps)

## Overview

This application showcases a movie management system where users can:
- Add new movies with title, director, and release year
- Rate movies on a scale of 0-5
- Edit existing movie entries
- Delete movies
- View all movies in a list format

The application uses TypeScript for type safety and IndexedDB for local browser storage, making it work offline and persist data between sessions.

## Prerequisites

- Node.js (v14 or higher)
- npm or pnpm (this project uses pnpm)
- Basic knowledge of TypeScript and HTML

## Project Setup

1. Create a new Vite project with TypeScript:
```bash
pnpm create vite ts-app --template vanilla-ts
cd ts-app
pnpm install
```

2. Install required dependencies:
```bash
pnpm add -D @types/node
```

## Step-by-Step Guide

### Step 1: Setting up the Project Structure

First, we need to set up the basic project structure:

```
src/
├── counter.ts           (Example file from Vite, can be ignored)
├── database.service.ts  (IndexedDB service)
├── main.ts              (Entry point)
├── movie.interface.ts   (TypeScript interface for Movie)
├── style.css            (Styling)
└── vite-env.d.ts        (Vite environment types)
```

### Step 2: Creating the Movie Interface

Let's define what a Movie object looks like in our system:

```typescript
// movie.interface.ts
export interface Movie {
    id?: number;        // Optional as it's auto-generated
    title: string;
    director: string;
    year: number;
    rating: number;     // Rating from 0-5
}
```

This interface will ensure type safety throughout our application when working with movie data.

### Step 3: Building the Database Service

The `DatabaseService` class handles all interactions with IndexedDB:

```typescript
// database.service.ts
import { Movie } from './movie.interface';

export class DatabaseService {
    private db: IDBDatabase | null = null;
    private readonly DB_NAME = 'MoviesDB';
    private readonly STORE_NAME = 'movies';

    constructor() {
        this.initDatabase();
    }

    public initDatabase(): Promise<void> {
        return new Promise((resolve, reject) => {
            const request = indexedDB.open(this.DB_NAME, 1);

            // Handle errors
            request.onerror = () => reject(request.error);
            
            // On successful opening
            request.onsuccess = () => {
                this.db = request.result;
                resolve();
            };

            // Create schema if needed (version upgrade)
            request.onupgradeneeded = (event) => {
                const db = (event.target as IDBOpenDBRequest).result;
                if (!db.objectStoreNames.contains(this.STORE_NAME)) {
                    const store = db.createObjectStore(this.STORE_NAME, { 
                        keyPath: 'id', 
                        autoIncrement: true 
                    });
                    store.createIndex('title', 'title', { unique: false });
                }
            };
        });
    }

    // CRUD Operations for Movies
    async addMovie(title: string, director: string, year: number): Promise<void> {
        const movie: Movie = { title, director, year, rating: 0 };
        return new Promise((resolve, reject) => {
            const transaction = this.db!.transaction([this.STORE_NAME], 'readwrite');
            const store = transaction.objectStore(this.STORE_NAME);
            const request = store.add(movie);

            request.onsuccess = () => resolve();
            request.onerror = () => reject(request.error);
        });
    }

    async updateMovie(id: number, title: string, director: string, year: number): Promise<void> {
        return new Promise((resolve, reject) => {
            const transaction = this.db!.transaction([this.STORE_NAME], 'readwrite');
            const store = transaction.objectStore(this.STORE_NAME);
            const request = store.get(id);

            request.onsuccess = () => {
                const data = request.result;
                if (data) {
                    data.title = title;
                    data.director = director;
                    data.year = year;
                    store.put(data);
                    resolve();
                }
            };
            request.onerror = () => reject(request.error);
        });
    }

    async rateMovie(id: number, rating: number): Promise<void> {
        return new Promise((resolve, reject) => {
            const transaction = this.db!.transaction([this.STORE_NAME], 'readwrite');
            const store = transaction.objectStore(this.STORE_NAME);
            const request = store.get(id);

            request.onsuccess = () => {
                const data = request.result;
                if (data) {
                    data.rating = rating;
                    store.put(data);
                    resolve();
                }
            };
            request.onerror = () => reject(request.error);
        });
    }

    async deleteMovie(id: number): Promise<void> {
        return new Promise((resolve, reject) => {
            const transaction = this.db!.transaction([this.STORE_NAME], 'readwrite');
            const store = transaction.objectStore(this.STORE_NAME);
            const request = store.delete(id);

            request.onsuccess = () => resolve();
            request.onerror = () => reject(request.error);
        });
    }

    async getAllMovies(): Promise<Movie[]> {
        return new Promise((resolve, reject) => {
            const transaction = this.db!.transaction([this.STORE_NAME], 'readonly');
            const store = transaction.objectStore(this.STORE_NAME);
            const request = store.getAll();

            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }
}
```

The service handles:
- Database initialization and schema creation
- Adding new movies
- Updating existing movies
- Rating movies
- Deleting movies
- Retrieving all movies

### Step 4: Setting up the UI

Now let's set up the main UI in our `main.ts` file:

```typescript
// main.ts
import './style.css'
import { DatabaseService } from './database.service'

// Create async initialization function
async function initializeApp() {
  const db = new DatabaseService();
  // Wait for DB to initialize
  await db.initDatabase();

  document.querySelector<HTMLDivElement>('#app')!.innerHTML = `
    <div class="container">
      <h1>Movie Management System</h1>
      
      <div class="add-movie-form">
        <h2>Add New Movie</h2>
        <input type="text" id="title" placeholder="Movie Title" />
        <input type="text" id="director" placeholder="Director" />
        <input type="number" id="year" placeholder="Year" />
        <button id="addMovie">Add Movie</button>
      </div>

      <div class="movie-list">
        <h2>Movies</h2>
        <div id="moviesList"></div>
      </div>
    </div>
  `;
  
  // Display movies function definition and other UI logic follows...
}

// Start the application
initializeApp().catch(console.error);
```

### Step 5: Implementing CRUD Operations

Next, we'll add event listeners and functions to handle the CRUD operations:

```typescript
// Inside initializeApp function in main.ts

// Update the displayMovies function
async function displayMovies() {
  const moviesList = document.querySelector('#moviesList')!;
  const movies = await db.getAllMovies();

  moviesList.innerHTML = movies.map(movie => `
      <div class="movie-card" id="movie-${movie.id}">
          <div class="movie-content">
              <h3>${movie.title}</h3>
              <p>Director: ${movie.director}</p>
              <p>Year: ${movie.year}</p>
              <p>Rating: ${movie.rating}/5</p>
              <div class="movie-actions">
                  <input type="number" min="0" max="5" placeholder="Rate (0-5)" class="rating-input" data-id="${movie.id}">
                  <button onclick="editMovie(${movie.id})">Edit</button>
                  <button onclick="deleteMovie(${movie.id})">Delete</button>
              </div>
          </div>
          <div class="edit-form" id="edit-${movie.id}" style="display: none;">
              <input type="text" class="edit-title" value="${movie.title}" placeholder="Movie Title">
              <input type="text" class="edit-director" value="${movie.director}" placeholder="Director">
              <input type="number" class="edit-year" value="${movie.year}" placeholder="Year">
              <button onclick="saveMovie(${movie.id})">Save</button>
              <button onclick="cancelEdit(${movie.id})">Cancel</button>
          </div>
      </div>
  `).join('');
}

// Add event listeners
document.querySelector('#addMovie')?.addEventListener('click', async () => {
  const title = (document.querySelector('#title') as HTMLInputElement).value;
  const director = (document.querySelector('#director') as HTMLInputElement).value;
  const year = parseInt((document.querySelector('#year') as HTMLInputElement).value);

  if (title && director && year) {
    await db.addMovie(title, director, year);
    await displayMovies();
    // Clear inputs
    (document.querySelector('#title') as HTMLInputElement).value = '';
    (document.querySelector('#director') as HTMLInputElement).value = '';
    (document.querySelector('#year') as HTMLInputElement).value = '';
  }
});

// Add event listener for rating changes
document.addEventListener('change', async (e) => {
  const target = e.target as HTMLInputElement;
  if (target.classList.contains('rating-input')) {
    const movieId = parseInt(target.dataset.id!);
    const rating = parseFloat(target.value);
    if (rating >= 0 && rating <= 5) {
      await db.rateMovie(movieId, rating);
      await displayMovies();
    }
  }
});

// Add functions for editing, canceling edits, saving changes, and deleting
window.deleteMovie = async (id: number) => {
  await db.deleteMovie(id);
  await displayMovies();
};

window.editMovie = (id: number) => {
  const movieCard = document.querySelector(`#movie-${id} .movie-content`)! as HTMLElement;
  const editForm = document.querySelector(`#edit-${id}`)! as HTMLElement;
  movieCard.style.display = 'none';
  editForm.style.display = 'block';
};

window.cancelEdit = (id: number) => {
  const movieCard = document.querySelector(`#movie-${id} .movie-content`)! as HTMLElement;
  const editForm = document.querySelector(`#edit-${id}`)! as HTMLElement;
  movieCard.style.display = 'block';
  editForm.style.display = 'none';
};

window.saveMovie = async (id: number) => {
  const editForm = document.querySelector(`#edit-${id}`)!;
  const title = (editForm.querySelector('.edit-title') as HTMLInputElement).value;
  const director = (editForm.querySelector('.edit-director') as HTMLInputElement).value;
  const year = parseInt((editForm.querySelector('.edit-year') as HTMLInputElement).value);

  if (title && director && year) {
    await db.updateMovie(id, title, director, year);
    await displayMovies();
  }
};

// Display movies immediately after initialization
await displayMovies();

// Type declaration for global functions
declare global {
  interface Window {
    deleteMovie: (id: number) => Promise<void>;
    editMovie: (id: number) => void;
    cancelEdit: (id: number) => void;
    saveMovie: (id: number) => Promise<void>;
  }
}
```

### Step 6: Styling the Application

Add styling to make the application look good:

```css
/* style.css - key parts */
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.add-movie-form {
  margin-bottom: 30px;
}

.add-movie-form input {
  margin: 5px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.movie-card {
  border: 1px solid #ccc;
  padding: 15px;
  margin: 10px 0;
  border-radius: 8px;
}

.movie-actions {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}

.rating-input {
  width: 60px;
  padding: 5px;
}

.edit-form {
  margin-top: 1rem;
  padding: 1rem;
  border-top: 1px solid #ccc;
}

.edit-form input {
  margin: 0.5rem;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
```

## Running the Application

To run the application:

```bash
pnpm run dev
```

This will start a development server, usually at http://localhost:5173/

## Key Learning Points

1. **TypeScript Integration**: Using interfaces for type safety
2. **IndexedDB**: Using a client-side database for persistent storage
3. **Promises**: Using async/await for asynchronous operations
4. **DOM Manipulation**: Safely working with DOM using TypeScript
5. **Event Handling**: Managing events with proper typing

## Next Steps

- Add search functionality
- Implement sorting (by rating, title, year)
- Add categories or tags for movies
- Implement user authentication
- Add movie poster uploads
- Implement data export/import functionality

---

Feel free to fork this project and extend it with your own features!
