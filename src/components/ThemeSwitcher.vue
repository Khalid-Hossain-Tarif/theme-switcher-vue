<script setup>
import { ref, watch } from 'vue';

const isDarkMode = ref(false);

watch(isDarkMode, (newVal) => {
    if (newVal) {
        document.documentElement.classList.add('dark');
    } else {
        document.documentElement.classList.remove('dark');
    }
}, { immediate: true });
</script>

<template>
    <div class="flex items-center">
        <label for="theme-switch" class="mr-2">Dark Mode:</label>
        <input type="checkbox" id="theme-switch" v-model="isDarkMode" class="form-checkbox h-5 w-5 text-blue-600" />
    </div>
</template>