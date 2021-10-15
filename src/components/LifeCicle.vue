<template>
    <h1>My name is: {{ name }}</h1>
</template>

<script>
export default {
    name: 'LifeCicle',
    data() {
        return {
            name: 'teste',
        }
    },
    created() {
        setTimeout(() => {
            this.name = 'Rafael'
        }, 1000);
    },
    mounted() {
        setTimeout(() => {
            this.name = 'Maya'
        }, 2000);  
    }
}
</script>

<style>

</style>