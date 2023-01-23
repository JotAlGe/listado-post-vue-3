<template>
    <div>
        <div class="grid">
            <div v-for="post in posts" :key="post.id">
                <h3> <span class="title-body">Title:</span> {{ post.title }}</h3>
                <p> <span class="title-body">Body:</span>{{ post.body }} </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            posts: []
        }
    },
    mounted() {
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then(response => response.json())
            .then(json => {
                this.posts = json
            })
    }
}
</script>

<style>
.title-body {
    font-size: 1.4rem;
    font-weight: bold;
}
</style>