<template>
    <nav>
        <router-link to="/">Home</router-link>
        <router-link :to="{name : 'AddProduct'}">Add Product</router-link>
    </nav>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
nav{
    margin: 60px 0;
    text-align: center;
}

nav a{
    text-decoration: none;
    margin-right: 15px;
    color: #252525;
}

.router-link-active{
    background-color: crimson;
    color: white;
    padding: 10px;
    border-radius: 5px;
}
</style>