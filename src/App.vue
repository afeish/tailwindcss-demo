<script setup>
import { Bars4Icon, HomeIcon, QuestionMarkCircleIcon, EnvelopeIcon, ClockIcon } from "@heroicons/vue/20/solid";
import { ref } from 'vue';
const recipes = ref([
  {
    id: 1,
    img: 'img/stew.jpg',
    name: '5 Bean Chili Stew',
    desc: 'Recipe by Mario',
    costTime: 30,
  },
  {
    id: 2,
    img: 'img/noodles.jpg',
    name: 'Veg Noodles',
    desc: 'Recipe by Mario',
    costTime: 10,
  },
  {
    id: 3,
    img: 'img/curry.jpg',
    name: 'Tofu curry',
    desc: 'Recipe by Mario',
    costTime: 25,
  },
])
const hidden = ref(true)
</script>

<template>
  <div class="grid md:grid-cols-10">
    <div class="md:col-span-1 md:flex md:justify-end">
      <nav class="text-right">
        <div class="flex justify-between items-center">
          <h1 class="font-bold uppercase p-4 border-b border-gray-100">
            <a href="/" class="hover:text-gray-800">Food Shop</a>
          </h1>
          <div :class="`px-4 cursor-pointer ${hidden ? 'md:hidden' : ''}`" id="burger" @click="hidden = !hidden">
            <Bars4Icon class="h-6 w-6 text-gray-500" />
          </div>
        </div>
        <ul class="text-sm mt-6 hidden md:block" id="menu">
          <li class="text-gray-700 font-bold py-1 border border-1 ">
            <a href="#" class="px-4 flex justify-end border-r-4 border-primary  items-center">
              <span class="border border-1 h-6 flex items-center justify-center">Home</span>
              <span
                class="material-symbols-outlined ml-2 border border-1 h-6 flex items-center justify-center text-gray-500 text-xl">
                home
              </span>
              <!-- <HomeIcon class="w-5 ml-2 text-gray-500" /> -->
            </a>
          </li>
          <li class="text-gray-700 font-bold py-1 flex justify-start">
            <a href="#" class="px-4 flex justify-end border-r-4 border-white">
              <span class="ml-2">About</span>
              <QuestionMarkCircleIcon class="w-5 ml-2 text-gray-500" />
            </a>
          </li>
          <li class="text-gray-700 font-bold py-1 flex justify-start">
            <a href="#" class="px-4 flex justify-end border-r-4 border-white">
              <span>Contact</span>
              <EnvelopeIcon class="w-5 ml-2 text-gray-500" />
            </a>
          </li>
        </ul>
      </nav>
    </div>

    <main class="px-16 py-6 md:col-span-9 bg-gray-100">
      <div class="flex justify-center md:justify-end">
        <a href="#"
          class="text-primary btn border-primary md:border-2 hover:bg-primary hover:text-white transition ease-out duration-500">Log
          in</a>
        <a href="#"
          class="text-primary ml-2 btn border-primary md:border-2 hover:bg-primary hover:text-white transition ease-out duration-500">Sign
          up</a>
      </div>

      <header>
        <h2 class="text-gray-700 text-6xl font-semibold">Recipes</h2>
        <h3 class="text-2xl font-semibold">For Customers</h3>
      </header>

      <div>
        <h4 class="font-bold pb-2 mt-12 border-b border-gray-200">
          Latest Recipes
        </h4>

        <div class="mt-8 grid lg:grid-cols-3 gap-10">
          <!-- cards go here -->
          <div class="card hover:shadow-lg" v-for=" recipe  in  recipes " :key="recipe.id">
            <img :src="recipe.img" alt="stew" class="h-32 sm:h-48 w-full object-cover" />
            <div class="m-4">
              <span class="font-bold">{{ recipe.name }}</span>
              <span class="block text-gray-500 text-sm">{{ recipe.desc }}</span>
            </div>
            <div class="badge flex items-center">
              <!-- <ClockIcon class="w-5 inline-block" /> -->
              <span class="material-symbols-outlined">
                timer
              </span>
              <span class="h-4">{{ recipe.costTime }} mins</span>
            </div>
          </div>
        </div>

        <h4 class="font-bold pb-2 mt-12 border-b border-gray-200">
          Most Popular
        </h4>

        <div class="mt-8">
          <!-- cards go here -->
        </div>
      </div>

      <div class="mt-12 flex justify-center">
        <div
          class="bg-secondary-100 text-secondary-200 btn hover:shadow-inner transform hover:scale-125 hover:bg-opacity-50 transition ease-out duration-300">
          Load more
        </div>
      </div>
    </main>
  </div>
</template>
