# Documentation

## CDN is not good choice

## Using postcss

- ```sh
     npm install -y
  ```

- - create css/tailwind.css file
  - in tailwind file add
    - @tailwind base
    - @tailwind components
    - @tailwind utilities

- যদি তুমি laravel , next.js অথবা vue ইউজ করে থাকেন তবে সবাই postcss ইউজ করে 🚀
- install tailwindcss ,postcss, autoprefixer এবং vite via npm . everyting will be dev dependency
  ```sh
     npm install -D tailwindcss postcss autoprefixer vite
  ```
- in package.json file change write "scripts" : {"dev" : "vite"}

  ```sh
    "scripts": {
  "dev": "vite"
     },
  ```

- generate postcss config and tailwind conf

  ```sh
  npx tailwindcss init -p
  ```

-

```
  sh
  npm run dev
```
