<template>
    <nav>
        <ul>
            <li>
                <router-link to='/' exact>
                    Blog
                </router-link>
            </li>
            <li>
                <router-link to='/add' exact>
                    Add a new Blog
                </router-link>
            </li>
        </ul>
    </nav>
</template>

<script>
export default {
    
}
</script>

<style scoped>
ul {
   list-style-type: none;
    text-align: center;
    margin: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
    
}

a{
    color: #fff;
    text-decoration: none;
    padding: 10px 12 px;
    border-radius: 10px;
    font-size: 24px;
    text-transform: capitalize;
}
nav {
    background: #444;
    padding: 20px;
    margin-bottom: 40px; 
    max-width: 960px;
    margin: 0 auto;
}
.router-link-active {
    background: #eee;
    color: #444;
    padding: 5px 8px;
}
</style>


