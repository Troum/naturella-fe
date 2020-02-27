<template lang="pug">
    b-row.m-0
        b-col.mx-auto( cols="10" )
            b-row( v-for="item in winners" :key="item.name")
                b-col.mx-auto.text-center.text-white.text-uppercase( cols="11" )
                    | {{ item.name }}
                b-col.mx-auto.text-center.text-white( cols="11" )
                    | {{ item.prize }}
</template>

<script>
    import axios from "axios"
    export default {
        data() {
          return {
              winners: []
          }
        },
        mounted() {
            axios.get('https://alidi-distribution.by/api/v1/winners')
            .then(response => {
                // eslint-disable-next-line no-console
                this.winners = response.data.winners;
            })
            .catch(() => {

            })
        }
    }
</script>

<style scoped>

</style>
