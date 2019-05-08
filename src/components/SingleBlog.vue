<template>
    <div id="single-blog">
        <div class="content">
        <h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
        </div>
    </div>
</template>

<script>
export default {
    name:"single-blog",
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
    },
    created(){
        this.$http.get('https://jsonplaceholder.typicode.com/posts/' + this.id)
        .then(function(data){
            // console.log(data);
            this.blog = data.body;
        });
    }
}
</script>

<style scoped>
#single-blog{
    min-width: 800px;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}
.content{
    background: #f9f9f9;
    border: 1px dotted #aaa;
    padding: 20px;
}
</style>
