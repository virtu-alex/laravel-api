<template>
    <section id="posts-list">
        <h2 class="my-3">Posts</h2>
        <AppLoader v-if="isLoading" />
        <div
            class="alert alert-danger alert-dismissible fade show"
            role="alert"
            v-else-if="error"
        >
            <p>{{ error }}</p>
            <button type="button" class="close" @click="error = null">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div v-else>
            <div v-if="posts.length">
                <PostCard v-for="post in posts" :key="post.id" :post="post" />
            </div>
            <h5 v-else>Non ci sono posts</h5>
        </div>
    </section>
</template>

<script>
import PostCard from "./PostCard.vue";
import AppLoader from "../AppLoader.vue";
export default {
    name: "PostsList",
    data() {
        return {
            posts: [],
            error: null,
            isLoading: false,
        };
    },
    components: { PostCard, AppLoader },
    methods: {
        fetchPosts() {
            this.isLoading = true;
            axios
                .get("http://localhost:8000/api/posts")
                .then((res) => {
                    this.posts = res.data;
                })
                .catch((err) => {
                    this.error = "Errore durante il fetch dei post";
                })
                .then(() => {
                    this.isLoading = false;
                });
        },
    },
    mounted() {
        this.fetchPosts();
    },
};
</script>
<style scoped lang="scss">

</style>
