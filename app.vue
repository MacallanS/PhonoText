<template>
    <NuxtLayout>
        <NuxtPage />
    </NuxtLayout>
</template>
<style lang="scss">
* {
    padding: 0;
    margin: 0;
    font-size: 1rem;
}

.element::-webkit-scrollbar {
    width: 0;
}

*:not(input, textarea) {
    user-select: none;
}

input,
textarea {
    user-select: text;
}

html {
    font-size: 62.5%;
    overflow-x: hidden;
}

body {
    margin: 0;
    font-family: Manrope, sans-serif;
}

h1 {
    font-size: 1.4rem;
}

h2 {
    font-size: 1.3rem;
}

h3 {
    font-size: 1.2rem;
}

h4 {
    font-size: 1.1rem;
}

h5 {
    font-size: 1rem;
}

a {
    color: black;
    text-decoration: none;
    outline: none;
}

input {
    display: block;
    box-sizing: border-box;
    background: none;
    border: none;
    border-radius: 0.15rem;
    outline: none;
    transition: 100ms;
}

button {
    display: block;
    box-sizing: border-box;
    text-align: center;
    background: none;
    border: none;
    border-radius: 0.2rem;
    outline: none;
    cursor: pointer;
    transition: 100ms;
}

ol,
ul {
    list-style: none;
}

.visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    border: 0;
    padding: 0;
    white-space: nowrap;
    clip-path: inset(100%);
    clip: rect(0 0 0 0);
    overflow: hidden;
}
</style>
