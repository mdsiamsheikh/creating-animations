<template>
    <div class="alert alert-success text-center">
        <h1>That's Correct!</h1>
        <hr>
        <button class="btn btn-primary" @click="onNextQueStion">Next Question</button>
    </div>
</template>
<style>

</style>
<script>

    export default{
        methods: {
            onNextQueStion() {
                this.$emit('confirmed');
            }
        }
    }
</script>