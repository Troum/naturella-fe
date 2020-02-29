<template lang="pug">
    b-row.m-0.p-0
        b-col.p-0.m-0.text-center.position-relative( cols="12" )
            img.img-fluid( src="@/assets/images/first-screen.svg" alt="Naturella" )
            b-button.button-register-anchor( type="button" size="lg" @click="$scrollTo('#registration')") Регистрация
        b-col.p-0.m-0.text-center.position-relative#rules( cols="12" )
            img.img-fluid( src="@/assets/images/m-mechanic.svg" alt="Naturella Mecanic" )
        b-col.p-0.m-0.text-center.position-relative#conditions( cols="12" )
            img.img-fluid( src="@/assets/images/m-gifts.svg" alt="Naturella Gifts" style="width: 100%" )
        b-col.m-0.p-0.text-center.position-relative( cols="12" )
            img.img-fluid( src="@/assets/images/m-register.svg" alt="Naturella Register" )
        b-col.m-0.p-0.text-center#registration( cols="12" )
            register-component.mt-3( :mobile="mobile" :needCheck="true" )
        b-col.m-0.p-0.text-center.position-relative#game( cols="12" )
            img.img-fluid( @click="getCoords" src="@/assets/images/m-footer.svg" style="width: 100%" alt="Naturella Register" )
</template>

<script>
    export default {
        props: {
            mobile: null
        },
        methods: {
            getCoords(event) {
                if(event.clientX >=157 && event.clientX <=224 && event.clientY >=460 && event.clientY <= 521){
                    window.open('tel:+375296081949', '_self');
                }
                if(event.clientX >=29 && event.clientX <=334 && event.clientY >=564 && event.clientY <= 590){
                    window.open('tel:+375296081949', '_self');
                }
                if(event.clientX >=273 && event.clientX <=334 && event.clientY >=360 && event.clientY <= 375){
                    this.$router.push({name: 'rules'})
                }

            }
        }
    }
</script>

<style scoped>

</style>
