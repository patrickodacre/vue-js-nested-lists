<template>
    <div class="box">
        <div class="card is-fullwidth" v-for="post in posts">
            <Post :post="post"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Post from './Post.vue'

export default {

    name: 'Posts',
    data() {
        return {
            posts: []
        }
    },
    created,
    components: {
        Post
    }

}
// Step 1: Life cycle hook, 'created' fires
function created() {
    // 1-1: Request posts from WordPress.com
    axios.get('https://public-api.wordpress.com/rest/v1.1/sites/stearns.wordpress.com/posts/')
        .then(( resp ) => {

            // 1-2: Save posts array to our data object.
            this.posts = resp.data.posts
        })
}
    
</script>

<style>

    .card-content {
        padding: 10px;
    }

    .content {
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-flow: row wrap;
    }

    .card-header-title {
        text-align: left;
    }
</style>