<template>
    <div class="box">
        <div class="card is-fullwidth" v-for="post in posts">
            <header class="card-header">
                <p class="card-header-title">
                    {{post.title}}
                </p>
                <a class="card-header-icon" @click.prevent="getLikes(post.ID)">
                    GET LIKES
                </a>
            </header>
            <div class="card-content" v-for="like in likes">
                <div class="content">
                    <div class="name">
                        {{like.first_name}}
                    </div>
                    <div class="notes">
                        <a :href="like.URL">website</a>
                    </div>
                    <div class="rating">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {

    name: 'Posts',
    data() {
        return {
            posts: [],
            likes: []
        }
    },
    created,
    methods: {
        getLikes
    }

}
// Step 1: Life cycle hook, 'created' fires
function created() {
    // 1-1: Request posts from WordPress.com
    axios.get('https://public-api.wordpress.com/rest/v1.1/sites/stearns.wordpress.com/posts/')
        .then(( resp ) => {
debugger
            // 1-2: Save posts array to our data object.
            this.posts = resp.data.posts
        })
}

// Step 2: get the likes for a specific post
function getLikes(postID) {

    // 2-1: Request the likes using the post ID
    axios.get(`https://public-api.wordpress.com/rest/v1.1/sites/stearns.wordpress.com/posts/${postID}/likes/`)
        .then((resp)=>{

            // 2-2 The array of likes is usually really long, so we just grab a few for our test
            this.likes = resp.data.likes.slice(0,3)
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