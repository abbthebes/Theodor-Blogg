<template>
    <div style="margin-left:10%; margin-right:10%;">
        <nuxt-content :document="post"></nuxt-content>
        <!-- <h1>{{ post.title }}</h1> -->
        <br>
        <h5>Author: {{ post.author}}</h5>
        <p>Created: {{ post.created}}</p> 
        <p>Updated: {{ post.updated}}</p>
        <br>
    </div>
</template>

<script>
export default {
    async asyncData({$content, params}){
        let post = await $content('postsmd/'+params.id).fetch();
        return {
            post
        }
    }
}

</script>




