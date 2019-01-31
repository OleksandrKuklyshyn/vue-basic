<template>

<div id="add-blog">
    <h2>Add a new Blog Post</h2>
    <form action="" v-if='!submitted'>
        <label for="">Blog Title</label>
        <input type="text" v-model.lazy="blog.title" required>
        <label for="">Blog Content</label>
        <textarea name="" id="" cols="30" rows="10" v-model="blog.content"></textarea>
        <div id="checkboxes">
            <label for="">Ninjas</label>
            <input type="checkbox" value="ninjas" v-model="blog.categories">
            <label for="">Wizards</label>
            <input type="checkbox" value="wizards" v-model="blog.categories">
            <label for="">Steve</label>
            <input type="checkbox" value="steve" v-model="blog.categories">
            <label for="">Cheese</label>
            <input type="checkbox" value="cheese" v-model="blog.categories">
        </div>
        <label for="">Author:</label>
        <select name="" id="" v-model='blog.author'>
            <option  v-bind:key="author" v-for='author in authors'>{{author}}</option>
            
        </select>
        <button v-on:click.prevent='post'>Add blog</button>
    </form>
    <div v-if='submitted'>
        <h3>Thanks a blod submitted</h3>
    </div>
    <div id="preview">
        <h3>Preview Blog</h3>
        <p>Blog Title: {{blog.title}}</p>
        <p>Blog contetnt: </p>
        <p>{{blog.content}}</p>
        <p>Blog Categories:</p>
        <ul >
            <li v-bind:key='category' v-for='category in blog.categories'>{{category}}</li>
        </ul>
        <p>Author: {{blog.author}}</p>
    </div>
</div>
</template>

<script>

export default {
 
 data(){
    return{ 
        blog: {
            title: '',
            content: '',
            categories: [

            ],
            author: ''
            
        },
        authors: [
            'The Net Ninja',
            'The Angular Avenger',
            'The Node Secret'
        ],
        submitted: false
    }
 },
 methods: {
     post: function(){
         this.$http.post('https://vue-first-project-2dd6f.firebaseio.com/posts.json',this.blog)
         .then(function(data){
             console.log(data)
             this.submitted = true
         });
     }
 }
}
</script>

<style lang="scss" scoped>
h2 {
    margin: 0 auto;
}
#add-blog *{
    box-sizing: border-box;
    
}
#add-blog{
    margin: 0 auto;
    max-width: 1000px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type='text'], textarea {
    display: block;
    width: 100%;
    padding: 8px;
}
#preview {
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes {
    margin-right: 10px;
    display: inline-block;
}
#checkboxes label {
    display: inline-block;
}
</style>