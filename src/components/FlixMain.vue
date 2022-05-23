<template>
    <div>
        <div class="card" v-for="(items, index) in items" :key="index">
            <h4> {{ items.title }}</h4>
            <h4>{{ items.name }}</h4>
            <h4>{{ items.original_name }}</h4>
            <h4>{{ items.original_title }}</h4>
            <country-flag country="item.original_language" />
            <h4>{{ divisioneArrotondata(items.vote_average) }}</h4>
            <star-rating v-model="voto" read-only="true"></star-rating>
            <img :src="`http://image.tmdb.org/t/p/w500/${items.poster_path}`" alt="">
        </div>

    </div>
</template>

<script>

import CountryFlag from 'vue-country-flag';
import StarRating from 'vue-star-rating';

export default {
    name: "FlixMain",
    components: {
        CountryFlag,
        StarRating,
    },
    props: {
        items: Array,
    },
    data: function () {
        return {
            voto: "",
        }
    },
    methods: {
        divisioneArrotondata(votoGrezzo) {
            let voto = 0
            voto = Math.ceil(votoGrezzo / 2)
            return voto

        }
    }
};


</script>

<style lang="scss">
@import "../style/common.scss";
</style>