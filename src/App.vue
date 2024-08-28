<template>
    <div class="app" id="app">
        <MainHeader></MainHeader>
        <div class="main"><router-view /></div>
        <MainFooter></MainFooter>
    </div>
</template>

<script setup>
import MainHeader from '@/components/MainHeader.vue';
import MainFooter from '@/components/MainFooter.vue';
</script>

<style>
body {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
}

.app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.main {
    flex: 1;
}
</style>
