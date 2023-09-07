<script setup>
import ThemeSwitcher from './ThemeSwitcher.vue';
</script>

<template>
    <header class="bg-gray-300 dark:bg-white px-10 py-2 flex items-center justify-between">
        <div>
            <router-link to="/" class="text-blue-600 font-semibold">Logo</router-link>
        </div>

        <ThemeSwitcher />

        <ul class="flex justify-end items-center gap-4">
            <li>
                <router-link to="/">Home</router-link>
            </li>
            <li>
                <router-link to="/about">About</router-link>
            </li>
            <li>
                <router-link to="/contact">Contact</router-link>
            </li>
        </ul>
    </header>
</template>