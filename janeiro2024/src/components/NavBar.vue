<template>
    <nav>
        <span>Primeiro site com Vue</span>
        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">Sobre</a></li>
            <li><a href="#">Login</a></li>
        </ul>
    </nav>
</template>

<script>
   
</script>

<style  scoped>
nav{
    background-color: #ccc;
    padding: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
ul{
    display: flex;
    list-style: none;
}
ul li{
    padding: 0 10px;
}
ul li a{
    text-decoration: none;
    color: #000;
}
</style>