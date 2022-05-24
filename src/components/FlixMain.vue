<template>
    <div>
        <div class="card" v-for="(item, index) in items" :key="index">
            <h4> {{ item.title }}</h4>
            <h4>{{ item.name }}</h4>
            <h4>{{ item.original_name }}</h4>
            <h4>{{ item.original_title }}</h4>
            <country-flag :country="item.original_language" />
            <h4>{{ divisioneArrotondata(item.vote_average) }}</h4>
            <!-- <star-rating v-model="voto" read-only="true"></star-rating> -->
            <span v-for="number in divisioneArrotondata(item.vote_average) " :key="number"> <i class="fas fa-star"> </i></span>
            <img :src="`http://image.tmdb.org/t/p/w500/${item.poster_path}`" alt="">
        </div>

    </div>
</template>

<script>

import CountryFlag from 'vue-country-flag';
// import StarRating from 'vue-star-rating';

export default {
    name: "FlixMain",
    components: {
        CountryFlag,
        // StarRating,
    },
    props: {
        items: Array,
    },
    data: function () {
        return {
        
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
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import "../style/common.scss";
</style>