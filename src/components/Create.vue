<template>
    <div>
        <h4 class="title-create">Create a post</h4>

        <form class="form" @submit.prevent="savePost">
            <label for="title">
                <input placeholder="Title..." v-model="title" id="title" type="text" class="title-post">
            </label>
            <label for="body">
                <input placeholder="Body..." v-model="body" id="body" type="text" class="body-post">
            </label>
            <button class="button-post" type="submit">Post</button>
            <span v-if="message" class="message-success"> {{ message }} </span>
        </form>
    </div>
</template>
<script>

export default {
    data() {
        return {
            title: '',
            body: '',
            message: ''
        }
    },
    methods: {
        async savePost() {
            try {
                const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
                    method: 'POST',
                    body: JSON.stringify({ title: this.title, body: this.body }),
                    headers: {
                        'Content-Type': 'application/json'
                    }
                })

                if (response.ok) {
                    this.message = '¡Post saved successfully!'
                    this.title = ''
                    this.body = ''
                }
                else throw new Error('¡Post failed!')
            } catch (e) {
                console.log(e);
            }
        }
    }
}

</script>
<style>
.title-create {
    font-size: 1.5rem;
    color: lightgray;
}

.form {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-gap: 16px;
    margin: 2%;
}

input,
button {
    font-weight: bold;
    border: none;
    border-radius: 15px;
    width: 250px;
    height: 50px;
    cursor: pointer;
}

.button-post {
    background-color: lightgreen;
    width: 40%;
}

.message-success {
    color: lightgreen
}
</style>