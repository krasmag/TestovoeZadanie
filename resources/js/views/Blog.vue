<template>
    <div>
        <spin v-if="loading"></spin>
        <div style="display:flex; flex-wrap: wrap;" v-else>
            <post
                v-for="post in posts"
                v-bind:key="post"
                v-bind:post="post"
                :title="post.name"
                :body="post.act"
                :date="post.created_at"
                :id="post.id"
            />
        </div>
    </div>
</template>

<script>
    import Spin from "../components/Spin";
    import axios from 'axios';
    import Post from "../components/Blog/Post";
    export default {
        components: {
            Spin,
            Post
        },
        data: () => ({
            loading: true,
            posts: []
        }),
        mounted() {
            this.loadPosts();
        },
        methods: {
            loadPosts() {
                axios.get('/api/main')
                .then(res => {
                    this.posts = res.data;
                    setTimeout(() => {
                        this.loading = false;
                    }, 500)
                })
            }
        }
    }
//     if(body == "true"){
//         body = "да"
// }else{
//     body = "нет"
// }
</script>

<style scoped>
    .uk-card {
        width: 40%;
        margin-right: 20px;
        margin-bottom: 20px;
    }

    .uk-card:last-child {
        margin-right: 0;
    }
</style>
