<script setup>
import ThemeSwitcher from './ThemeSwitcher.vue';
</script>

<template>
    <header class="bg-gray-300 dark:bg-white px-10 py-3 flex items-center justify-between">
        <div>
            <router-link to="/" class="text-blue-600 font-semibold text-2xl">LOGO</router-link>
        </div>

        <ThemeSwitcher />

        <ul class="flex justify-end items-center gap-4">
            <li>
                <router-link to="/" class="text-base font-medium transition-all" active-class="text-blue-600">Home</router-link>
            </li>
            <li>
                <router-link to="/about" class="text-base font-medium transition-all" active-class="text-blue-600">About</router-link>
            </li>
            <li>
                <router-link to="/contact" class="text-base font-medium transition-all" active-class="text-blue-600">Contact</router-link>
            </li>
        </ul>
    </header>
</template>