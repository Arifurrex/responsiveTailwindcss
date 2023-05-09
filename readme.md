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

  - default: h1 er font size hobe text-2xl(24px ) এবং sm:text-4xl(36 px) এবং

  - font-weight hobe font-bold

- p
  - defalut : p font আছে তাই আর sm:text-xl(20px) হবে

# lg breakpont(sm 640px @media (min-width: 640px) { ... })

lg breakpoint onek khali space dekacce
ami cacci image ek pase takbe ar content ek pashe takbe

![Screenshot 2023-03-30 195409](https://user-images.githubusercontent.com/48369328/228864916-0e901490-a04e-46d5-9ad5-7e6d888632f4.png)

![Screenshot 2023-03-30 195409](https://user-images.githubusercontent.com/48369328/228862907-139b10ad-1208-496e-8966-d642abce4082.png)

img কে lg:hidden করে দিলাম ।
আলাদা div এ image নিলাম hidden করে দিলাম আর lg:block করে দিলাম

```sh

<div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl">
      <img class="h-10" src="img/twitch.png" alt="" />
      <img
        class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
        src="img/workonremote.webp"
        alt=""
      />
      <h1 class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl">
        You can work on anywhere .
        <span class="text-red-500">Take advantage of it</span>
      </h1>
      <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
        Twitch will helps you find work-friendly rentals in beautiful so you can
        enjoy some niece weather even when your're not on vacation
      </p>
      <div class="mt-4 sm:mt-6">
        <a
          class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
          href=""
          >Book your space</a
        >
      </div>
    </div>

    <div>
      <img class="hidden lg:block" src="img/workonremote.webp" alt="" />
    </div>

```

- flex er maddome amra split korte pari কিংবা grid er maddome amra split korte pari । আমরা এখানে grid এর মদ্যমে split করব

- এই container টা কে আমরা div এর মদ্যের wrap করব

```sh
<div class="grid grid-cols-2">
      <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl">
        <img class="h-10" src="img/twitch.png" alt="" />
        <img
          class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
          src="img/workonremote.webp"
          alt=""
        />
        <h1 class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl">
          You can work on anywhere .
          <span class="text-red-500">Take advantage of it</span>
        </h1>
        <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
          Twitch will helps you find work-friendly rentals in beautiful so you
          can enjoy some niece weather even when your're not on vacation
        </p>
        <div class="mt-4 sm:mt-6">
          <a
            class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
            href=""
            >Book your space</a
          >
        </div>
      </div>

      <div>
        <img class="hidden lg:block" src="img/workonremote.webp" alt="" />
      </div>
    </div>

```

![Screenshot 2023-03-30 203000](https://user-images.githubusercontent.com/48369328/228869500-f269b610-b2d0-4184-9740-3c9bc408adfa.png)

- h1

  - default: h1 er font size hobe
  - text-2xl(24px ) এবং
  - sm:text-4xl(36 px) এবং
  - lg:text-3xl(30px)

  - font-weight hobe font-bold

- p
  - defalut : p font আছে তাই আর sm:text-xl(20px) হবে

```sh
<div class="grid grid-cols-2">
      <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 py-48">
        <img class="h-10" src="img/twitch.png" alt="" />
        <img
          class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
          src="img/workonremote.webp"
          alt=""
        />
        <h1
          class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl"
        >
          You can work on anywhere .
          <span class="text-red-500">Take advantage of it</span>
        </h1>
        <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
          Twitch will helps you find work-friendly rentals in beautiful so you
          can enjoy some niece weather even when your're not on vacation
        </p>
        <div class="mt-4 sm:mt-6">
          <a
            class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
            href=""
            >Book your space</a
          >
        </div>
      </div>

      <div>
        <img class="hidden lg:block" src="img/workonremote.webp" alt="" />
      </div>
    </div>

```

![Screenshot 2023-03-30 204312](https://user-images.githubusercontent.com/48369328/228874358-225a5a28-9cc3-4cb9-9a18-47563cf7fb77.png)

### কিভাবে image full and space nibe with relative and absulate

```sh
<body class="bg-slate-200">
    <div class="bg-gray-300 grid grid-cols-2">
      <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 py-48">
        <img class="h-10" src="img/twitch.png" alt="" />
        <img
          class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
          src="img/workonremote.webp"
          alt=""
        />
        <h1
          class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl"
        >
          You can work on anywhere .
          <span class="text-red-500">Take advantage of it</span>
        </h1>
        <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
          Twitch will helps you find work-friendly rentals in beautiful so you
          can enjoy some niece weather even when your're not on vacation
        </p>
        <div class="mt-4 sm:mt-6">
          <a
            class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
            href=""
            >Book your space</a
          >
        </div>
      </div>

      <div class="hidden relative lg:block">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>
  </body>

```

### problem: larger breakpoint e tik ace but smaller breakpoint e designe ভেঙে গেছে

নিচের দিকে breakpoint এ সব gird-cols-2 ডেকাচ্ছে

![Screenshot 2023-03-30 205550](https://user-images.githubusercontent.com/48369328/228878044-e800d3f3-849a-46dc-a269-71d568f6970f.png)

so grid container e lg:grid-cols-2 dile ei sommar solution hobe . specify kore dite hobe grid-cols-2 ta lg er jonne

```sh

<body class="bg-slate-200">
    <div class="bg-gray-300 grid lg:grid-cols-2">
      <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 lg:py-48">
        <img class="h-10" src="img/twitch.png" alt="" />
        <img
          class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
          src="img/workonremote.webp"
          alt=""
        />
        <h1
          class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl"
        >
          You can work on anywhere .
          <span class="text-red-500">Take advantage of it</span>
        </h1>
        <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
          Twitch will helps you find work-friendly rentals in beautiful so you
          can enjoy some niece weather even when your're not on vacation
        </p>
        <div class="mt-4 sm:mt-6">
          <a
            class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
            href=""
            >Book your space</a
          >
        </div>
      </div>

      <div class="hidden relative lg:block">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>
  </body>

```

### sm:max-w-md to lg:max-w-full

![Screenshot 2023-03-30 211120](https://user-images.githubusercontent.com/48369328/228882687-3ef0fdd6-b76b-478b-918f-3e741b1e1adb.png)

```sh
<div class="bg-gray-300 grid lg:grid-cols-2">
      <div
        class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 lg:py-48 lg:max-w-full"
      >
        <img class="h-10" src="img/twitch.png" alt="" />
        <img
          class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
          src="img/workonremote.webp"
          alt=""
        />
        <h1
          class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl"
        >
          You can work on anywhere .
          <span class="text-red-500">Take advantage of it</span>
        </h1>
        <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
          Twitch will helps you find work-friendly rentals in beautiful so you
          can enjoy some niece weather even when your're not on vacation
        </p>
        <div class="mt-4 sm:mt-6">
          <a
            class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
            href=""
            >Book your space</a
          >
        </div>
      </div>

      <div class="hidden relative lg:block">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>

```

# xl breakpont (xl 1280px @media (min-width: 1280px) { ... })

```
sm	640px	@media (min-width: 640px) { ... }
md	768px	@media (min-width: 768px) { ... }
lg	1024px	@media (min-width: 1024px) { ... }
xl	1280px	@media (min-width: 1280px) { ... }
2xl	1536px	@media (min-width: 1536px) { ... }

```

- h1

  - default: h1 er font size hobe
  - text-2xl(24px ) এবং
  - sm:text-4xl(36 px) এবং
  - lg:text-3xl(30px)
  - xl:text-4xl(36px)

  - font-weight hobe font-bold

- p
  - defalut : p font আছে তাই আর sm:text-xl(20px) হবে

### xl:max-w-xl set on content

```sh

<div class="bg-gray-300 grid lg:grid-cols-2">
      <div
        class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 lg:py-48 lg:max-w-full"
      >
        <div class="xl:max-w-xl">
          <img class="h-10" src="img/twitch.png" alt="" />
          <img
            class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
            src="img/workonremote.webp"
            alt=""
          />
          <h1
            class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl xl:text-4xl"
          >
            You can work on anywhere .
            <br class="hidden lg:inline" />
            <span class="text-red-500">Take advantage of it</span>
          </h1>
          <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
            Twitch will helps you find work-friendly rentals in beautiful so you
            can enjoy some niece weather even when your're not on vacation
          </p>
          <div class="mt-4 sm:mt-6">
            <a
              class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
              href=""
              >Book your space</a
            >
          </div>
        </div>
      </div>

      <div class="hidden relative lg:block">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>

```

### xl:mr-0

```sh
  <div class="bg-gray-300 grid lg:grid-cols-2">
      <div
        class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 lg:py-48 lg:max-w-full xl:mr-0"
      >
        <div class="xl:max-w-xl">
          <img class="h-10" src="img/twitch.png" alt="" />
          <img
            class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
            src="img/workonremote.webp"
            alt=""
          />
          <h1
            class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl xl:text-4xl"
          >
            You can work on anywhere .
            <br class="hidden lg:inline" />
            <span class="text-red-500">Take advantage of it</span>
          </h1>
          <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
            Twitch will helps you find work-friendly rentals in beautiful so you
            can enjoy some niece weather even when your're not on vacation
          </p>
          <div class="mt-4 sm:mt-6">
            <a
              class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
              href=""
              >Book your space</a
            >
          </div>
        </div>
      </div>

      <div class="hidden relative lg:block">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>

```

# 2xl breakpoint

### 2xl:grid-cols-5 2xl:col-span-2 2xl:col-span-3

```sh
<div class="bg-gray-300 grid lg:grid-cols-2 2xl:grid-cols-5">
      <div
        class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:px-12 lg:py-48 lg:max-w-full xl:mr-0 2xl:col-span-2"
      >
        <div class="xl:max-w-xl">
          <img class="h-10" src="img/twitch.png" alt="" />
          <img
            class="mt-6 rounded-lg shadow-xl sm:mt-8 sm:h-64 sm:w-full object-cover object-center lg:hidden"
            src="img/workonremote.webp"
            alt=""
          />
          <h1
            class="mt-6 text-2xl font-bold text-gray-900 sm:mt-8 sm:text-4xl lg:text-3xl xl:text-4xl"
          >
            You can work on anywhere .
            <br class="hidden lg:inline" />
            <span class="text-red-500">Take advantage of it</span>
          </h1>
          <p class="mt-2 text-gray-600 sm:mt-4 sm:text-xl">
            Twitch will helps you find work-friendly rentals in beautiful so you
            can enjoy some niece weather even when your're not on vacation
          </p>
          <div class="mt-4 sm:mt-6">
            <a
              class="inline-block bg-red-500 text-white px-5 py-3 rounded-lg font-semibold font-medium shadow-lg shadow-red-400 uppercase tracking-widest sm:text-base"
              href=""
              >Book your space</a
            >
          </div>
        </div>
      </div>

      <div class="hidden relative lg:block 2xl:col-span-3">
        <img
          class="absolute inset-0 w-full h-full object-cover object-center"
          src="img/workonremote.webp"
          alt=""
        />
      </div>
    </div>

```
