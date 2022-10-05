<template>
    <div class="card bg-dark text-white mb-3">
        <div class="card-body">
            <h5 class="card-title">
                {{ post.title }}
            </h5>
            <h6 class="card-subtitle mb-2 text-muted">
                Pubblicato il: {{ publishedAt }}
            </h6>
            <p>
                {{ post.content }}
            </p>
            <div
                class="card-footer d-flex justify-content-between align-items-center"
            >
                <span
                    class="badge badge-pill"
                    :class="`badge-${post.category ? post.category.color : 'light'}`"
                >
                    {{ post.category ? post.category.label : "nessuna" }}</span
                >

                <div>
                    <span
                        v-for="tag in post.tags"
                        :key="tag.id"
                        class="badge mr-1 text-white"
                        :style="`background-color:${tag.color}`"
                    >
                        {{ tag.label }}
                    </span>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "PostCard",
    props: {
        post: Object,
    },
    computed: {
        publishedAt() {
            const postDate = new Date(this.post.created_at);
            let day = postDate.getDate();
            let month = postDate.getMonth() + 1;
            const year = postDate.getFullYear();
            if (day < 10) day = "0" + day;
            if (month < 10) month = "0" + month;
            return `${day}/${month}/${year}`;
        },
    },
};
</script>
<style lang=""></style>
