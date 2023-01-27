<template>
    <div>
        <h4 class="title-create">Create a post</h4>

        <div class="form">
            <label for="title">
                <input id="title" type="text" class="title-post">
            </label>
            <label for="body">
                <input id="body" type="text" class="body-post">
            </label>
            <button class="button-post">Post</button>
        </div>
    </div>
</template>
<script>

export default {

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
}

.button-post {
    background-color: lightgreen;
    width: 40%;
}
</style>