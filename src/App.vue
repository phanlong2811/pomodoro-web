<template>
    <div id="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/setting">Setting</router-link>
        <router-link to="/about">About</router-link>
    </div>
    <router-view />
</template>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

#nav {
    margin: 20px;
    padding: 30px;
    a {
        color: #df645f;
        padding: 5px 15px;
        border-radius: 10px;
        border: none;
        font: {
            weight: bold;
        }
        text : {
            decoration: none;
        }
        &.router-link-exact-active {
            background-color: #df645f;
            color: white;
        }
    }
    a:hover {
        cursor: pointer;
    }
}
</style>
