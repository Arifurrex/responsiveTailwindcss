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

## mobile designe

![Screenshot 2023-03-28 220417](https://user-images.githubusercontent.com/48369328/228300566-e5ebfbc1-e2c8-4eb3-9ac4-459a7e66f02a.png)

### tips :

. যদি parent এর মদ্যের childrenগলো কে space দিতে হয় তবে spacey-4 দিতে হবে
. BUTTON e inline-block দিলে padding এর spaceing golo টিক তকবে

## make it responsive

এখন যদি screen সাইজ বড় করেন তবে ডেকতে পাবেন ইমেজ অনেক বড় হয়ে গেছে । its weird

![Screenshot 2023-03-29 215148](https://user-images.githubusercontent.com/48369328/228596274-3a086d3b-8c0b-4b85-a6e8-06d5c495a50b.png)

max-w-md mane div er width max-width bole dilam 448px
div টা কে center করতে mx-auto করে দিলাম

![Screenshot 2023-03-30 000144](https://user-images.githubusercontent.com/48369328/228627834-90fdea6b-78e6-4577-8e60-5ee93bc35751.png)

but এখানে problem হল div টার max-width:448px হওয়ায় লার্জ ডিসপ্লে তে অনেক স্পেস খালি দেখাছে

তাহলে any display তে div টা কিভাবে ভাল দেখাবে
breakpoint

tailwind css এর ৫ টা breakpoint আছে

```
sm	640px	@media (min-width: 640px) { ... }
md	768px	@media (min-width: 768px) { ... }
lg	1024px	@media (min-width: 1024px) { ... }
xl	1280px	@media (min-width: 1280px) { ... }
2xl	1536px	@media (min-width: 1536px) { ... }

```

div er width 640 er upore max-widht hobe max-w-xl

![Screenshot 2023-03-29 215148](https://user-images.githubusercontent.com/48369328/228632767-b80286e4-a88b-4255-b667-441b9acd879b.png)

default setting er por প্রথমে sm device er jonne set korbo
then md er breakpoint set korbo
then lg er breakpoint er jonno set korbo
after that xl er
finally 2xl

- h1
  . default: h1 er font size hobe text-2xl(২৪ px ) এবং sm:text-4xl(36 px) এবং

  . font-weight hobe font-bold

-p
. defalut : p font আছে তাই আর sm:text-xl(20px) হবে
