<template>
    <div class="container">
        <h1 class="preview-header">Превью введенных данных</h1>
        <div v-if="user.name || user.age">
            <p class="parent-data">{{ user.name }}, {{ user.age }} лет</p>
        </div>
        <div v-if="children.length">
            <h2 class="preview-header">Дети</h2>
            <div v-for="(child, index) in children" :key="index">
                <div class="child-data">
                    {{ child.name }}, {{ child.age }} лет
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const user = ref({});
const children = ref([]);

onMounted(() => {
    const savedData = localStorage.getItem('formData');
    if (savedData) {
        const parsedData = JSON.parse(savedData);
        user.value = parsedData.user;
        children.value = parsedData.children;
    }
});
</script>

<style scoped>
.container {
    max-width: 616px;
    margin: auto;
    color: rgb(17, 17, 17);
}

.preview-header {
    font-size: 16px;
    font-weight: 500;
    margin-top: 30px;
}

.parent-data {
    margin-top: 20px;
    margin-bottom: 60px;
    font-size: 16px;
    font-weight: 700;
}

.child-data {
    border-radius: 5px;
    background: rgb(241, 241, 241);
    width: max-content;
    padding: 10px 20px;
    font-size: 16px;
    font-weight: 700;
    margin-bottom: 20px;
}
</style>
