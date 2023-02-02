<template>
    <small v-if="successMessage" class="deleteMessage">{{ successMessage }}</small>
    <div class="grid-container">
        <div v-for="post in posts" :key="post.id" class="grid-item">
            <div class="card">
                <div class="card-header">
                    {{ post.title }}
                    <button class="delete" @click="deletePost(post.id)">-</button>
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
            posts: [],
            successMessage: ''
        }
    },
    async mounted() {
        const response = await fetch('https://jsonplaceholder.typicode.com/posts')
        const posts = await response.json()
        this.posts = posts
    },
    methods: {
        async deletePost(id) {
            try {
                const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`, {
                    method: 'DELETE'
                });
                const data = response.json();
                this.posts.splice(id, 1);
                this.successMessage = 'Post deleted successfully'
                console.log(data);
            } catch (e) {
                console.log(e);
            }
        }
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

    display: flex;
    justify-content: space-between;
}

.card-body {
    font-size: 14px;
}

.delete {
    background-color: red;
    width: 20px;
    height: 20px
}

.deleteMessage {
    color: green;
    font-size: 1.5rem;
    font-weight: bold;
}
</style>