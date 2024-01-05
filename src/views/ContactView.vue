<script setup>
import MainLayout from '../components/MainLayout.vue';

// Page Title of Views
const pageTitle = 'Contact'
</script>

<template>
  <MainLayout :pageTitle="pageTitle">
    <section class="container mx-auto mt-8 p-4">
      <h1 class="text-3xl font-bold mb-4">Contact Us</h1>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
       
        <div class="text-gray-700">
          <p class="mb-4"><strong>Email:</strong> calvintumulak10@gmail.com</p>
          <p class="mb-4"><strong>Phone:</strong> Phone:09321649363</p>
          <p><strong>Address:</strong> Mahayahay, Marigondon Lapu-Lapu City </p>
        </div>
      </div>
    </section>
  </MainLayout>
</template>
