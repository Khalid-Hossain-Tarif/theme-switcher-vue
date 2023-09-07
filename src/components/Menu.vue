<script setup>
import ThemeSwitcher from './ThemeSwitcher.vue';
</script>

<template>
    <div class="bg-gray-300 dark:bg-white px-10 py-2 flex items-center justify-between">
        <div>
            <a class="text-blue-600 font-semibold">Logo</a>
        </div>

        <ThemeSwitcher />

        <ul class="flex justify-end items-center gap-4">
            <li>
                <router-link>Home</router-link>
            </li>
            <li>
                <router-link>About</router-link>
            </li>
            <li>
                <router-link>Contact</router-link>
            </li>
        </ul>
    </div>
</template>