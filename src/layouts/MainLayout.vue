<script setup>
import Footer from './Footer.vue';
import Navbar from './Navbar.vue';

</script>

<template>
    <div>
        <Navbar />
        <RouterView class="min-h-[calc(100vh-16rem)] py-15.5 max-w-7xl mx-auto"/>
        <Footer />
    </div>
</template>