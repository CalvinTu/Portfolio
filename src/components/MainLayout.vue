<script setup>
import { onMounted } from 'vue';
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';

const props = defineProps({
    pageTitle: String,
});

onMounted(() => {
    // Page Title
    document.title = props.pageTitle + ' - ' + 'My Portfolio';
})
</script>

<template>
    <Header />

    <main class="mx-auto max-w-screen-xl px-12 py-6">
        <slot />
    </main>

    <Footer />
</template>