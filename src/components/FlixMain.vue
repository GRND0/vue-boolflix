<template>
    <div>
        <div class="wrapper">
            <div class="card" v-for="(item, index) in items" :key="index">
                <div class="wrapper-info" :class="{invisibile: nascosto}"  >
                    <h4 v-if="item.title"> Titolo : {{ item.title }}</h4>
                    <h4 v-else> Titolo : {{ item.name }}</h4>
                    <h4 v-if="item.original_name"> Titolo originale : {{ item.original_name }}</h4>
                    <h4 v-else> Titolo originale : {{ item.original_title }}</h4>
                    <country-flag :country="item.original_language" />
                    <h5> Voto {{ divisioneArrotondata(item.vote_average) }}</h5>
                    <!-- <star-rating v-model="voto" read-only="true"></star-rating> -->
                    <span v-for="number in divisioneArrotondata(item.vote_average) " :key="number"> <i
                            class="fas fa-star">
                        </i></span>
                    <span class="descrizione">{{item.overview}}</span>    
                </div>
                <img class="wrapper-flip" v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w500/${item.poster_path}`" alt="">
                <div class="placeholder" v-else>
                <h2>NO POSTER</h2>
                </div>
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
    background-color: #1e2d3b;
    overflow-y: scroll;
    color: lightgray;

    .card {
        width: calc(100% / 6 - 2rem);
        height: 420px;
        margin: 0.5rem;
        background-color: #394a5a;
        // border: solid 1px white;
        box-shadow: 5px 5px 5px rgba($color: black, $alpha: 0.3);
        overflow-y: hidden;
        


        .wrapper-info {
            padding: 0.5rem;
            color: white;
        }

        img {
            object-fit: cover;
            height: 100%;
            width: 100%;
        }

        .descrizione {
            display: block;
        }

    }

    .fa-star {
        color: gold;
    }

    .placeholder {
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;

        
    }

}
</style>