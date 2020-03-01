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
    export default {
        data() {
          return {
              winners: []
          }
        },
        mounted() {
            this.$http.get('api/v1/old-winners')
            .then(response => {
                this.winners = response.data.winners;
            })
            .catch(() => {

            })
        }
    }
</script>

<style scoped>

</style>
