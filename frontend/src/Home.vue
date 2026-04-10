<template>
    <nav>
        <router-link to="/">Didier & Brigitte</router-link>
        <div class="liens">
            <router-link to="/click-and-collect">Click and Collect</router-link>
            <router-link to="/contact">Contact</router-link>
        </div>
    </nav>
</template>

<style scoped>
nav {
    display: flex;
    font-size: 30px;
}

.liens a{
    margin-right:50px;
}

nav a {
    text-decoration: none;
    color: black;
    margin-right:50px;
}
</style>