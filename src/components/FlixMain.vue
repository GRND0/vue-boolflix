<template>
    <div>
        <div class="wrapper">
            <div class="card" v-for="(item, index) in items" :key="index">
                <div class="wrapper-info" :class="{invisibile: nascosto}"  >
                    <h4> Titolo : {{ item.title }}</h4>
                    <h4> TItolo : {{ item.name }}</h4>
                    <h4> Titolo originale : {{ item.original_name }}</h4>
                    <h4> TItolo originale : {{ item.original_title }}</h4>
                    <country-flag :country="item.original_language" />
                    <h4> Voto {{ divisioneArrotondata(item.vote_average) }}</h4>
                    <!-- <star-rating v-model="voto" read-only="true"></star-rating> -->
                    <span v-for="number in divisioneArrotondata(item.vote_average) " :key="number"> <i
                            class="fas fa-star">
                        </i></span>
                </div>
                <img class="wrapper-flip" :src="`http://image.tmdb.org/t/p/w500/${item.poster_path}`" alt="">
            </div>
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
            nascosto : true 

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

.card .wrapper-info {
    display: none;
}

.card:hover .wrapper-info {
    display: block;
}

.card:hover .wrapper-flip {
    display: none;
}

.invisibile {
    display: none;
}

.wrapper {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    height: calc(100vh - 50px);
    padding: 1rem;
    background-color: black;
    overflow-y: scroll;

    .card {
        width: calc(100% / 6 - 2rem);
        margin: 0.5rem;
        background-color: darkgrey;
        border: solid 1px white;

    }

}
</style>