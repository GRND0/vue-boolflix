<template>
    <div>
        <div class="card" v-for="(items, index) in items" :key="index">
            <h2> {{ items.title }}</h2>
            <h2>{{ items.original_title }}</h2>
            <h2>{{items.original_language}}</h2>
            <h2>{{items.vote_average}}</h2>
        </div>

    </div>
</template>

<script>
export default {
    name: "FlixMain",
    props: {
        items: Array,
    },
}
</script>

<style lang="scss">
@import "../style/common.scss";
</style>