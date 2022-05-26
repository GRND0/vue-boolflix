<template>
    <div class="header">
        <div class="logo"><img src="../assets/c072857f28ffed69c9266a55183f4c20.png" alt=""></div>
        <div class="wrapper-ricerca">
            <input type="text" placeholder="Cerca film o serie TV" v-model="ricerca">
            <button @click="$emit('search', ricerca)">Cerca</button>
        </div>
    </div>
</template>

<script>



export default {
    name: "FlixHeader",
    data: function () {
        return {
            ricerca: "",
        };
    },
}
</script>

<style lang="scss">
@import "../style/common.scss";

.header {
    height: 50px;
    width: 100%;
    display: flex;
    background-color: black;
    align-items: center;
    justify-content: space-between;
    border-bottom: 2px solid gray;

    .logo {
        height: 70%;
        margin-left: 2rem;

        img {
            height: 100%;
        }
    }

    .wrapper-ricerca {
        margin-right: 2rem;

        button {
            background-color: red;
            color: white;
            border-radius: 5px;
            border: none;
            padding: 0.2rem;
        }

        input {
            margin: 1rem;
            border-radius: 5px;
            border: none;
            padding: 0.2rem;
        }
    }
}
</style>