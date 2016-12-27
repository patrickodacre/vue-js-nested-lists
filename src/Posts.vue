<template>
    <div class="box">
        <!-- iterate over our posts, passing each Post object to its own Post.vue component. -->
        <div class="card is-fullwidth" v-for="post in posts">
            <Post :post="post"/> <!-- pass the post object to the Post.vue component. -->
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
        Post // our imported Post component must be wired up here on the Posts options object under the 'components' property.
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

</style>