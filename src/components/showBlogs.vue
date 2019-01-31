<template>
    <div id='show-blogs' v-theme>
        <h1>All Blog Articles</h1>
        <input type="text" v-model="search" placeholder="search blogs">
        <div class="single-blog" v-bind:key="blog" v-for='blog in fileredBlogs'>
            <router-link v-bind:to="'/blog/'+ blog.id">
                <h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
            </router-link>
            <article>{{blog.content | snippet }}</article>
        </div>
    </div>
</template>
<script>
export default {
    data: function(){
        return {
            blogs: [],
            search: ''
        }
    },
    methods: {

    },
    created(){
        this.$http.get('https://vue-first-project-2dd6f.firebaseio.com/posts.json').then(function(data){
           return data.json();
            
        }).then(function(data){
            var blogsArray =[];
            for( let key in data){
                data[key].id=key;
                blogsArray.push(data[key]);
            }
            this.blogs =blogsArray;
        })
    },
    computed: {
        fileredBlogs: function(){
            return this.blogs.filter((blog)=> {
                return blog.title.match(this.search)
            })
        }
    },
    filters: {
        toUppercase(value) {
            return value.toUpperCase()
        }
    },
    
        
    }

</script>

<style >
#show-blogs {
    max-width: 960px;
    margin: 0 auto;
    box-sizing: border-box;
    padding: 0;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
    
}
a {
    text-decoration:none;
}
a:hover {
    text-decoration-line:underline;
    text-decoration-color:darkmagenta;
}
#show-blogs input {
    width: 94%;
    margin: 10px 0;
    border-radius: 30px;
    border: 2px solid #444444;
    padding: 10px 0 10px 40px;
    
    font-size: 20px;
    text-transform: capitalize;

}
input:hover {
    border: 4px solid #446644;
}
h1{
    text-align: center;
}
</style>

