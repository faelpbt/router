<template>
    <h1>Meu nome é {{ name }} e trabalho com {{ profissao }}</h1>
</template>

<script>
export default {
    name: 'FirstComponent',
    data() {
        return{
            name: 'Rafael',
            profissao: 'programador',
        }
    },
}
</script>