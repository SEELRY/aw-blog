<template>
    <nav>
        <ul>
            <li>
                <router-link to="/" exact>文章列表</router-link>
                <router-link to="/add" exact>添加文章</router-link>
            </li>
        </ul>
    </nav>    
</template>

<script>
export default {
    name:"blog-header"
}
</script>

<style scoped>
ul{
    list-style-type: none;
    text-align: center;
    margin: 0;
}
li{
    display: inline-block;
    margin: 0 10px;
}
a{
    color: #fff;
    text-decoration: none;
    padding: 12px;
    border-radius: 5px;
}
nav{
    background: #1487ed;
    padding: 30px 0;
    margin-bottom: 40px;
}
.router-link-active{
    background: rgba(255,255,255,0.3);
    color: #0f6bbb;
}
</style>
