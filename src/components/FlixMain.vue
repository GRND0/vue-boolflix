<template>
    <div>
        <div class="card" v-for="(items, index) in items" :key="index">
            <h4> {{ items.title }}</h4>
            <h4>{{ items.original_title }}</h4>
            <country-flag country="item.original_language" />
            <h4>{{items.vote_average}}</h4>
        </div>

    </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
    name: "FlixMain",
    components : {
        CountryFlag,
    },
    props: {
        items: Array,
    },
}
</script>

<style lang="scss">
@import "../style/common.scss";
</style>