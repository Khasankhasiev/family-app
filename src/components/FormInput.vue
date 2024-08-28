<template>
    <div class="input-container">
        <input :value="modelValue" :type="type" @input="updateValue($event)" />
        <label for="name">{{ labelValue }}</label>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
    modelValue: {
        type: [String, Number],
    },
    labelValue: {
        type: String,
    },
    type: {
        String,
    },
});

// Определение события, которое компонент испускает
const emit = defineEmits(['update:modelValue']);

// Обработчик события input
function updateValue(event) {
    emit('update:modelValue', event.target.value);
}
</script>

<style scoped>
.input-container {
    position: relative;
    max-width: 616px;
}

.input-container input {
    width: 100%;
    padding-top: 26px;
    padding-left: 16px;
    padding-bottom: 6px;
    font-size: 18px;
    border: none;
    border-bottom: 1px solid #ccc;
    outline: none;
    transition: border-color 0.3s;
}

.input-container input:focus,
.input-container input:not(:placeholder-shown) {
    border: 1px solid rgb(241, 241, 241);
    border-radius: 4px;
}

.input-container label {
    position: absolute;
    top: 0;
    left: 0;
    padding: 10px 0;
    font-size: 16px;
    color: #aaa;
    pointer-events: none;
    transition: all 0.3s;
}

.input-container input:focus + label,
.input-container input:not(:placeholder-shown) + label {
    top: -5px;
    left: 16px;
    font-size: 13px;
    color: rgba(17, 17, 17, 0.48);
}
</style>
