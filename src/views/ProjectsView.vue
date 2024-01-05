<script setup>
import MainLayout from '../components/MainLayout.vue';

// Page Title of Views
const pageTitle = 'Projects'
</script>

<template>
  <MainLayout :pageTitle="pageTitle">
    <section>
      <div class="grid grid-cols-2 gap-4 md:grid-cols-3  ">
        <!-- image - start -->
        <router-link to="/SnakeGame" href="#" class="group relative flex h-48 items-end overflow-hidden rounded-lg bg-gray-100 shadow-lg md:h-80">            <img src="../assets/OIP.jpg"
                loading="lazy" alt=""
                class="absolute inset-0 h-full w-full object-cover object-center transition duration-200 group-hover:scale-110" />

            <div
                class="pointer-events-none absolute inset-0 bg-gradient-to-t from-gray-800 via-transparent to-transparent opacity-50">
            </div>

            <span class="relative ml-4 mb-3 inline-block text-sm text-white md:ml-5 md:text-lg">Now is Time to Play</span>
        </router-link>
        <!-- image - end -->

       
    </div>
    </section>
  </MainLayout>
</template>