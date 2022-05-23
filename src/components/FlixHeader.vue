<template>
    <div>
        <input type="text" placeholder="Cerca film o serie TV" v-model="ricerca">
        <button @click="$emit('search', ricerca)">Cerca</button>
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
</style>