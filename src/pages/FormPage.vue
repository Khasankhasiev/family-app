<template>
    <div class="container">
        <h1 class="form-header">Персональные данные</h1>
        <div class="form-info">
            <FormInput
                v-model.trim="user.name"
                label-value="Имя"
                type="text"
            ></FormInput>
            <FormInput
                v-model.trim="user.age"
                label-value="Возраст"
                type="number"
            ></FormInput>
        </div>
        <div class="form-child">
            <div class="form-child_header-wrapper">
                <h2 class="form-header">Дети(макс. 5)</h2>
                <button
                    class="button add-button"
                    v-if="children.length < 5"
                    @click="addChild"
                >
                    <span class="icon">+</span>Добавить ребенка
                </button>
            </div>

            <div
                class="child-actions"
                v-for="(child, index) in children"
                :key="index"
            >
                <FormInput
                    class="child-input"
                    v-model.trim="child.name"
                    label-value="Имя:"
                    type="text"
                ></FormInput>
                <FormInput
                    v-model.trim="child.age"
                    label-value="Возраст"
                    type="number"
                ></FormInput>
                <button class="delete-button" @click="removeChild(index)">
                    Удалить
                </button>
            </div>
        </div>
        <button class="button save-button" @click="saveData">Сохранить</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

import FormInput from '@/components/FormInput.vue';

const user = ref({
    name: '',
    age: null,
});

const children = ref([]);

const router = useRouter();

const addChild = () => {
    if (children.value.length < 5) {
        children.value.push({ name: '', age: null });
    }
};

const removeChild = index => {
    children.value.splice(index, 1);
};

const saveData = () => {
    const data = {
        user: user.value,
        children: children.value,
    };

    localStorage.setItem('formData', JSON.stringify(data));

    router.push({ name: 'preview' });
};
</script>

<style scoped>
.container {
    max-width: 616px;
    margin: auto;
    padding-top: 30px;
}

.form-header {
    color: rgb(17, 17, 17);
    font-size: 16px;
    font-weight: 600;

    margin-bottom: 20px;
}

.form-info {
    display: flex;
    flex-direction: column;
    gap: 10px;

    margin-bottom: 33px;
}

.form-child_header-wrapper {
    display: flex;
    justify-content: space-between;
    margin-bottom: 11px;
}

.child-actions {
    display: flex;
    gap: 34px;
    margin-bottom: 11px;
}

.child-input {
    max-width: 228px;
}

/* стили для кнопки */
.button {
    padding: 10px 20px;
    font-size: 14px;
    border: 2px solid #00aaff;
    border-radius: 100px;
    cursor: pointer;
    font-family: 'Montserrat', sans-serif;
    transition: background-color 0.3s, color 0.3s;
}

.add-button {
    display: flex;
    align-items: center;
    color: #00aaff;
    background-color: white;
}

.add-button .icon {
    font-size: 25px;
    margin-right: 8px;
}

.add-button:hover {
    background-color: #00aaff;
    color: white;
}

.add-button:hover .icon {
    color: white;
}

.save-button {
    background-color: #00aaff;
    color: white;
}
.save-button:hover {
    background-color: #0995db;
}
.save-button:active {
    background-color: #088bcc;
}

.delete-button {
    background-color: transparent;
    outline: none;
    border: none;
    cursor: pointer;
    color: rgb(1, 167, 253);
}
</style>
