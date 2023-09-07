<!-- <script setup>
import { ref, watch } from 'vue';

const isDarkMode = ref(false);

watch(isDarkMode, (newVal) => {
    if (newVal) {
        document.documentElement.classList.add('dark');
    } else {
        document.documentElement.classList.remove('dark');
    }
}, { immediate: true });
</script> -->

<script setup>
import { ref, watch } from 'vue';

const isDarkMode = ref(false);

// Detect the system theme and set isDarkMode accordingly
const systemThemeMediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
isDarkMode.value = systemThemeMediaQuery.matches;

// Watch for changes in isDarkMode and update the system theme
watch(isDarkMode, (newVal) => {
  document.documentElement.classList.toggle('dark', newVal);
});

// Watch for changes in the system theme preference and update isDarkMode
systemThemeMediaQuery.addEventListener('change', (event) => {
  isDarkMode.value = event.matches;
});

// Function to toggle the system theme
const toggleSystemTheme = () => {
  isDarkMode.value = systemThemeMediaQuery.matches;
};
</script>

<template>
    <div class="flex items-center gap-4">
        <div class="flex items-center">
            <label for="theme-switcher" class="mr-2">Dark Mode:</label>
            <input type="checkbox" id="theme-switcher" v-model="isDarkMode" class="form-checkbox h-5 w-5 text-blue-600" />
        </div>

        <button @click="toggleSystemTheme" class="text-blue-600">
            System Theme
        </button>
    </div>
</template>