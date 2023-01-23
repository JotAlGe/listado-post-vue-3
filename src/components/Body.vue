<template>
    <div class="grid-container">
        <div v-for="post in posts" :key="post.id" class="grid-item">
            <div class="card">
                <div class="card-header">
                    {{ post.title }}
                </div>
            </div>
            <div class="card-body">
                <p>{{ post.body }} </p>
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
.grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-gap: 16px;
}

.grid-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 5% 0 5%;
    justify-content: center;
    border: 1px solid green;
    border-radius: 25px;
}

.card {
    width: 300px;
    padding: 16px;

}

.card-header {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 8px;
}

.card-body {
    font-size: 14px;
}
</style>