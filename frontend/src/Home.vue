<template>
    <nav class="flex flex-col gap-4 p-4 text-2xl md:flex-row md:items-center md:justify-between md:text-3xl">
        <router-link to="/" class="tracking-wide text-black no-underline">
            Didier & Brigitte
        </router-link>
        <div class="flex flex-col gap-3 text-xl md:flex-row md:gap-8 md:text-2xl">
            <router-link to="/click-and-collect" class="text-black no-underline transition-opacity hover:opacity-70">
                Click and Collect
            </router-link>
            <router-link to="/contact" class="text-black no-underline transition-opacity hover:opacity-70">
                Contact
            </router-link>
        </div>
    </nav>
</template>