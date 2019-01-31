<template>
    <div class="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.content}}</article>
    </div>
</template>
<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            blog: {}
        }
    },
    created() {
        this.$http.get('https://vue-first-project-2dd6f.firebaseio.com/posts/'+ this.id+'.json').then(
            function(data){
                return data.json();

            }
        ).then(function(data){
            this.blog = data;
        })
    }    
}
</script>
<style>
.single-blog{
  max-width: 1000px;  
  margin: 0 auto;
  padding: 10px 30px 10px 30px;
}


</style>

