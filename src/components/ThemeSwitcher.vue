<!-- <script setup>
import { ref, watch } from 'vue';

const isDarkMode = ref(false);

const systemThemeMediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
isDarkMode.value = systemThemeMediaQuery.matches;

watch(isDarkMode, (newVal) => {
    document.documentElement.classList.toggle('dark', newVal);
});

systemThemeMediaQuery.addEventListener('change', (event) => {
    isDarkMode.value = event.matches;
});

const toggleSystemTheme = () => {
    isDarkMode.value = systemThemeMediaQuery.matches;
};
</script> -->

<script setup>
import { ref, watch, onMounted } from 'vue';

const isDarkMode = ref(false);

const updateTheme = (darkMode) => {
  document.documentElement.classList.toggle('dark', darkMode);
  localStorage.setItem('darkMode', darkMode ? '1' : '0');
};

watch(isDarkMode, (newVal) => {
  updateTheme(newVal);
});

const systemThemeMediaQuery = window.matchMedia('(prefers-color-scheme: dark)');

systemThemeMediaQuery.addEventListener('change', (event) => {
  isDarkMode.value = event.matches;
});

const toggleSystemTheme = () => {
  isDarkMode.value = systemThemeMediaQuery.matches;
  updateTheme(isDarkMode.value);
};

onMounted(() => {
  const storedTheme = localStorage.getItem('darkMode');
  if (storedTheme === '1') {
    isDarkMode.value = true;
  }
});
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

        <button id="header__indeterminate" @click="toggleSystemTheme" title="Switch to dark mode"
            class="relative w-10 h-10 focus:outline-none focus:shadow-outline text-gray-500">
            <svg style="width:30px;height:30px" viewBox="0 0 24 24">
                <path fill="currentColor"
                    d="M12 2A10 10 0 0 0 2 12A10 10 0 0 0 12 22A10 10 0 0 0 22 12A10 10 0 0 0 12 2M12 4A8 8 0 0 1 20 12A8 8 0 0 1 12 20V4Z" />
            </svg>
        </button>
    </div>
</template>


<!-- Icons -->
<!-- <div class="ml-4">
    <button id="header__sun" title="Switch to system theme"
        class="relative w-10 h-10 focus:outline-none focus:shadow-outline text-gray-500">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-sun" width="24" height="24"
            viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round"
            stroke-linejoin="round">
            <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
            <circle cx="12" cy="12" r="4"></circle>
            <path
                d="M3 12h1m8 -9v1m8 8h1m-9 8v1m-6.4 -15.4l.7 .7m12.1 -.7l-.7 .7m0 11.4l.7 .7m-12.1 -.7l-.7 .7">
            </path>
        </svg>
    </button>
    <button id="header__moon" title="Switch to light mode"
        class="relative w-10 h-10 focus:outline-none focus:shadow-outline text-gray-500">
        <svg style="width:24px;height:24px" viewBox="0 0 24 24">
            <path fill="currentColor"
                d="M17.75,4.09L15.22,6.03L16.13,9.09L13.5,7.28L10.87,9.09L11.78,6.03L9.25,4.09L12.44,4L13.5,1L14.56,4L17.75,4.09M21.25,11L19.61,12.25L20.2,14.23L18.5,13.06L16.8,14.23L17.39,12.25L15.75,11L17.81,10.95L18.5,9L19.19,10.95L21.25,11M18.97,15.95C19.8,15.87 20.69,17.05 20.16,17.8C19.84,18.25 19.5,18.67 19.08,19.07C15.17,23 8.84,23 4.94,19.07C1.03,15.17 1.03,8.83 4.94,4.93C5.34,4.53 5.76,4.17 6.21,3.85C6.96,3.32 8.14,4.21 8.06,5.04C7.79,7.9 8.75,10.87 10.95,13.06C13.14,15.26 16.1,16.22 18.97,15.95M17.33,17.97C14.5,17.81 11.7,16.64 9.53,14.5C7.36,12.31 6.2,9.5 6.04,6.68C3.23,9.82 3.34,14.64 6.35,17.66C9.37,20.67 14.19,20.78 17.33,17.97Z" />
        </svg>
    </button>
</div> -->