# Setting-up a TS project

---

### **Step 1: Install Node.js and npm**

Before setting up TypeScript, make sure you have **Node.js** and **npm** (Node Package Manager) installed. You can verify their installation by running:

```bash
node -v
pnpm -v
```

If you haven't installed them, download and install Node.js from [Node.js Download](https://nodejs.org/).

---

### **Step 2: Initialize a Node.js Project**

1. Create a new directory for your project:

   ```bash
   mkdir my-ts-project
   cd my-ts-project
   ```

2. Initialize the Node.js project:

   ```bash
   npm init -y
   ```
   or 
    ```bash
   pnpm init -y
    ```

   This creates a `package.json` file with default values.

---

### **Install TypeScript**

You need to install **TypeScript** for compiling `.ts` .

1. Install TypeScript:

   ```bash
   pnpm add -D typescript tsx
   ```

### **Create `tsconfig.json` File**

The `tsconfig.json` file is used to configure how TypeScript compiles your code. You can generate a `tsconfig.json` with default settings by running:

```bash
pnpx tsc --init
```

Alternatively, you can manually create a `tsconfig.json` file with the following configuration:

```json
{
  "compilerOptions": {
    "target": "es5",                       // Target JavaScript version (ES5 for wide compatibility)
    "module": "commonjs",                   // Module system (CommonJS for Node.js)
    "strict": true,                         // Enable strict type-checking options
    "esModuleInterop": true,                // Allows default imports from CommonJS modules
    "jsx": "react",                         // Enable JSX support for React in .tsx files
    "skipLibCheck": true,                   // Skip type checking of declaration files
    "outDir": "./dist",                     // Output directory for compiled JavaScript
    "rootDir": "./src",                     // Root directory for source files
    "forceConsistentCasingInFileNames": true // Ensure consistent casing in file names
  },
  "include": [
    "src/**/*.ts",    // Include all .ts files
    "src/**/*.tsx"    // Include all .tsx files (for React)
  ],
  "exclude": [
    "node_modules"    // Exclude node_modules from the compilation process
  ]
}
```

### Key Options in `tsconfig.json`:

* **`jsx`**: Set to `react` for projects using JSX (e.g., React). This ensures `.tsx` files are compiled correctly.
* **`target`**: JavaScript version to compile to, such as `es5` or `es6`.
* **`outDir`**: Directory to store compiled JavaScript files.
* **`rootDir`**: Directory where your TypeScript source files are located (`src`).
* **`include`**: Specifies that `.ts` and `.tsx` files in the `src` folder should be compiled.
* **`strict`**: Enables strict type-checking to help catch errors early.

---



### **Compile TypeScript to JavaScript**

To compile your TypeScript code, run the TypeScript compiler (`tsc`) in the terminal:

```bash
npx tsc
```
or 
```bash
pnpx tsc
```


### **Add Build and Start Scripts (Optional)**

You can add custom scripts to your `package.json` file to make the compilation process easier.

1. Open `package.json` and add the following under `"scripts"`:

   ```json
   "scripts": {
      "dev": "tsx watch index.ts", // run the code in dev mode
     "build": "tsc",         // Compile TypeScript files
     "start": "node dist/index.js"  // Run compiled JavaScript for Node.js projects
   }
   ```

   2. Now you can run the following commands:

       * * **Run TypeScript Code in dev **:
           ```Bash
           pnpm run dev
           ```
       * **Compile TypeScript**:

         ```bash
         pnpm run build
         ```
       * **Run the compiled JavaScript**:

         ```bash
         pnpm start
         ```
