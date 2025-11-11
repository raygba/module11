<template>
    <div id="header">
        <router-link id="logo" to="/">Random Quotes</router-link>
        <nav>
            <router-link to="/">Quote Generator</router-link>
            <router-link :to="{ name: 'about' }">About</router-link>
            <router-link :to="{ name: 'contact' }">Contact</router-link>
        </nav>
    </div>
</template>