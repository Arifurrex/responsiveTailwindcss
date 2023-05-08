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

```sh
  npm run dev
```
## designe starting
```sh
  <body>
    <div class="px-8 py-12">
      <img class="h-10" src="img/twitch.png" alt="" />
      <img
        class="mt-6 rounded-lg shadow-xl"
        src="img/workonremote.webp"
        alt=""
      />
      <h1 class="mt-6 text-2xl font-bold text-gray-900">
        You can work on anywhere .
        <span class="text-red-500">Take advantage of it</span>
      </h1>
      <p class="mt-4 text-gray-600">
        Twitch will helps you find work-friendly rentals in beautiful so you can
        enjoy some niece weather even when your're not on vacation
      </p>
      <div class="mt-4">
        <a
          class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest"
          href=""
          >Book your space</a
        >
      </div>
    </div>
  </body>
```
## mobile designe

div এর element গলো viewport এর edge এর সাথে লেগে আছে

![Screenshot 2023-03-29 211223](https://user-images.githubusercontent.com/48369328/228586022-7a351032-862a-4f40-abb0-c7174383bfce.png)

px-8 এবং py-12 দিলে div এর element গলো edge থেকে স্পেস নিবে

```
px-8 py-12
```

![Screenshot 2023-03-28 220417](https://user-images.githubusercontent.com/48369328/228300566-e5ebfbc1-e2c8-4eb3-9ac4-459a7e66f02a.png)

### tips :

. যদি parent এর মদ্যের childrenগলো কে space দিতে হয় তবে spacey-4 দিতে হবে
. BUTTON e inline-block দিলে padding এর spaceing golo টিক তকবে
. tracking-widest মানে letter-spacing=0.1em
