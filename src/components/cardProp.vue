<template>

    <ul class="border ms-1 mt-3">
        <li><strong>Titolo:</strong> {{ title }}</li>
        <li><strong>Titolo Originale:</strong> {{ originalTitle }}</li>
        <li><strong>Lingua:</strong> {{ lang }}</li>
        <li><strong>Voto:</strong> {{ vote }}</li>
    </ul>

</template>

<script>
export default {
    name: 'cardProp',
    props:{
        title: String,
        originalTitle: String,
        lang: String,
        vote: Number,
    }
}
</script>

<style scoped lang="scss">
@import '@/style/utilities';

</style>