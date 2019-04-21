<template>
  <div class="add-blog">
      <h2>添加文章Add-Blog</h2>
      <form v-if="!submmited">
          <label>文章标题</label>
          <input type="text" v-model="blog.title" required />
          
          <label>文章内容</label>
          <textarea v-model="blog.content"></textarea>

          <div id="checkboxes">
              <label>Vue.js</label>
              <input type="checkbox" value="Vue.js" name="" id="" v-model="blog.categories">
              <label>Node.js</label>
              <input type="checkbox" value="Node.js" name="" id="" v-model="blog.categories">
              <label>React.js</label>
              <input type="checkbox" value="React.js" name="" id="" v-model="blog.categories">
              <label>Angular.js</label>
              <input type="checkbox" value="Angular.js" name="" id="" v-model="blog.categories">
          </div>
          <label>作者：</label>
          <select v-model="blog.author">
              <option v-for="author in authors">
                  {{author}}
              </option>
          </select>
          <p>作者：{{blog.author}}</p>
          <button v-on:click.prevent="post">添加文章</button>
      </form>
      <div v-if="submmited">
        <h3>文章发布成功！</h3>
      </div>
      <hr>
      <div id="preview">
          <h3>文章总揽</h3>
          <p>文章标题：{{blog.title}}</p>
          <p>文章内容：</p>
          <p>{{blog.content}}</p>
          <p>博客分类：</p>
          <ul>
              <li v-for="category in blog.categories">{{category}}</li>
          </ul>
          <p>作者：{{blog.author}}</p>
      </div>
  </div>
</template>

<script>
export default {
  //https://jsonplaceholder.typicode.com/

  name: 'app-blog',
  data () {
    return {
      blog:{
          title:"",
          content:"",
          categories:[],
          author:"",
          message:''
      },
      authors:["Hemiah","Henry","Bucky"],
      submmited:false
    }
  },
  methods:{
      post:function(){
        this.$http.post("https://jsonplaceholder.typicode.com/posts",{
          title:this.blog.title,
          body:this.blog.content,
          userId:1
        })
          .then(function(data){
            console.log(data);
            this.submmited = true;
          });
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
