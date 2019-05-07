<template>
  <div id="show-blogs">
      <h1>文章列表</h1>
      <input type="text" v-model="search" placeholder="搜索">
      <div v-for="blog in filteredBlogs" class="single-blog">
          <h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
          <article>{{blog.body | snippet}}</article>
      </div>
  </div>
</template>

<script>

export default {
  name: 'show-blogs',
  data(){
      return {
          blogs:[],
          search:""
      }
  },
  created(){
      this.$http.get('../../static/posts.json')
      .then(function(data){
        //   console.log(data);
        this.blogs = data.body.slice(0,10);
        console.log(this.blogs);
      })
  },
  computed:{
      filteredBlogs:function(){
          return this.blogs.filter((blog) => {
              return blog.title.match(this.search);
          })
      }
  },
  filters:{
      "to-uppercase":function(value){
          return value.toUpperCase();
      },
      "snippet":function(value){
          return value.slice(0,100) + "...";
      }
    //   ,
    //   toUppercase(value){
    //       return value.toUpperCase();
    //   }
  },
  directives:{
      'rainbow':{
          bind(el,binding,vnode){
              el.style.color = "#" + Math.random().toString(16).slice(2,8);
          }
      }
  }
}
</script>

<style>
#show-blogs{
    min-width: 800px;
    margin: 0 auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: rgb(243, 243, 243);
}
</style>
