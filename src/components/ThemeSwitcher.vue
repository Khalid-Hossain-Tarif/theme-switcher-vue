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
    <div class="flex items-center gap-4">
        <div class="flex items-center">
            <label for="theme-toggle" class="cursor-pointer">
                <input type="checkbox" id="theme-toggle" v-model="isDarkMode" class="hidden" />
                <div class="toggle-wrapper bg-black w-14 h-7 rounded-full p-1 relative transition-all">
                    <div class="toggle-thumb bg-white w-5 h-5 rounded-full absolute left-1 transition-all"></div>
                </div>
            </label>
        </div>
    </div>
</template>