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

![Screenshot 2023-05-09 152117](https://github.com/Arifurrex/responsiveTailwindcss/assets/48369328/98073a60-bbb8-4ddc-b280-215a8d959b26)

### tips :

. যদি parent এর মদ্যের childrenগলো কে space দিতে হয় তবে spacey-4 দিতে হবে
. BUTTON e inline-block দিলে padding এর spaceing golo টিক তকবে



## make it responsive

### set max-w-md 
এখন যদি screen সাইজ বড় করেন তবে দেখতে পাবেন ইমেজ ও content অনেক large হয়ে গেছে । 

![Screenshot 2023-05-09 152247](https://github.com/Arifurrex/responsiveTailwindcss/assets/48369328/7ce041a7-bce3-404f-a29b-32682c4ad627)

এখন যদি screen সাইজ বড় করেন তবে দেখতে পাবেন ইমেজ ও কন্টেন্ট অনেক বড় হয়ে গেছে । its weird দেখতে তাই আমরা 
div max-w-md মানে div er max-width:448px বলে দিলাম এবং 
div টা কে center করতে mx-auto করে দিলাম । এতে পুরো div এর maximum width হবে 448 px । এবং mx-auto দেযায় margin-left:auto ;margin-right:auto হবে মানে div টা center এ হবে । 

![Screenshot 2023-03-30 000144](https://user-images.githubusercontent.com/48369328/228627834-90fdea6b-78e6-4577-8e60-5ee93bc35751.png)

### max-w-md is problem in large screen
but এখানে problem হল div টার max-w-md বা max-width:448px হওয়ায় লার্জ ডিসপ্লে তে অনেক স্পেস খালি দেখাছে

তাহলে any display তে div টা কিভাবে ভাল দেখাবে

*breakpoint
tailwind css এর ৫ টা breakpoint আছে

```
sm	640px	@media (min-width: 640px) { ... }
md	768px	@media (min-width: 768px) { ... }
lg	1024px	@media (min-width: 1024px) { ... }
xl	1280px	@media (min-width: 1280px) { ... }
2xl	1536px	@media (min-width: 1536px) { ... }

```

in breakpoint div এর width 640px বা sm এর উপরে হলে maximum width হবে max-w-xl বা max-width:512px 

* max-width *
```sh
max-w-0	max-width: 0rem; /* 0px */
max-w-none	max-width: none;
max-w-xs	max-width: 20rem; /* 320px */
max-w-sm	max-width: 24rem; /* 384px */
max-w-md	max-width: 28rem; /* 448px */
max-w-lg	max-width: 32rem; /* 512px */
max-w-xl	max-width: 36rem; /* 576px */

```

### কোন breakpoint নিয়ে আগে কাজ করব ? breakpoint sequence :
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

### min-width: 640px বা sm breakpoint এ :

640px এর উপরের breakpoint এ অনেক খালি space দেখাচ্ছে । আমি চাচ্ছি image এক পাশে থাকবে আর content অন্য পাশে থাকবে ।  


![Screenshot 2023-05-10 004028](https://github.com/Arifurrex/responsiveTailwindcss/assets/48369328/1d52fcaa-96a7-433e-9866-4dd82c1ecf5f)


![Screenshot 2023-05-10 010013](https://github.com/Arifurrex/responsiveTailwindcss/assets/48369328/b53bba23-ed48-4fde-9268-d8b02dbde90e)

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
