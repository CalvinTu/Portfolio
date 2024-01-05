<template>
    <section class="flex gap-6 py-16">
      <!-- Left Side -->
      <div class="w-1/4 flex flex-col items-center justify-center">
        <router-link to="/projects" href="#"
          class="group relative flex h-64 w-96 items-end overflow-hidden rounded-lg bg-gray-100 shadow-lg md:h-80 md:w-120">
          <img src="../assets/calvin.jpg"
            loading="lazy" alt="Clcky"
            class="absolute inset-0 h-full w-full object-cover object-center transition duration-200 group-hover:scale-110" />
  
          <div
            class="pointer-events-none absolute inset-0 bg-gradient-to-t from-gray-800 via-transparent to-transparent opacity-50">
          </div>
  
          <span class="relative ml-4 mb-3 inline-block text-sm text-white md:ml-5 md:text-lg">Ride it slow</span>
        </router-link>
      </div>
  
      <!-- Middle Section (with Lorem text) -->
      <div class="w-1/2 mx-auto">
        <h1 class="text-4xl font-bold text-gray-800 text-center">Hi, Calvin Tumulak</h1>
        <p class="text-lg text-gray-600 text-center">BSIT Student 4-B</p>
        <p class="text-lg text-gray-600 text-center">
          Web developer and Programming
        </p>
  
        <div class="mt-4 text-center">
          <router-link to="/todolist" class="inline-block rounded-lg bg-pink-500 text-white px-4 py-2 text-center text-sm font-semibold text-gray-500 outline-none ring-indigo-300 transition duration-100 hover:bg-pink-600 focus-visible:ring active:bg-pink-700 md:px-8 md:py-3 md:text-base">Todolist</router-link>
        </div>
  
        <div class="flex mt-4 space-x-4">
          <!-- Facebook Icon -->
          <a :href="FacebookLink" target="_blank" class="social-link">
            <i class="fab fa-facebook"></i>
          </a>
          <!-- Instagram Icon -->
          <a :href="InstagramLink" target="_blank" class="social-link">
            <i class="fab fa-instagram"></i>
          </a>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  const FacebookLink = 'https://www.facebook.com/calvinadales/';
  const InstagramLink = 'https://www.instagram.com/clvntmlk/';
  </script>
  