<template lang="pug">
    b-row.m-0.p-0
        b-col.p-0.text-center.position-relative( cols="12" )
            b-row.m-0.p-0
                b-col.mx-auto.p-0.always_greeting( cols="10" )
                    b-row.m-0.p-0.position-relative
                        b-col.mx-auto.p-0.text-center( cols="10" )
                            img.img-fluid( src="@/assets/images/girl.png" alt="Naturella" )
                        b-col.always_greeting_text( cols="5" )
                            h1.text-uppercase.font-weight-bold.text-white.text-left Купи naturella и выиграй поездку
                                br
                                span( style="font-size: 135%" ) в будапешт
                            b-button( type="button" size="lg" ) Регистрация
        b-col.p-0.text-center.position-relative#rules( cols="12" )
            b-col.mx-auto.p-0( cols="12" )
                b-row.m-0.p-0.position-relative
                    b-col.mx-auto.p-0.text-center( cols="10" )
                        img.img-fluid( src="@/assets/images/mechanic.svg" alt="Naturella Mechanic" )
        b-col.p-0.text-center.position-relative#conditions( cols="12" )
            b-col.mx-auto.p-0( cols="12" )
                b-row.m-0.p-0.position-relative
                    b-col.mx-auto.p-0.text-center( cols="10" )
                        img.img-fluid( src="@/assets/images/gift.svg" alt="Naturella Gift" )
        b-col.p-0.text-center.position-relative.always_registration_background.min-vh-100#registration( cols="12" )
            register-component( :mobile="mobile" :needCheck="true" )
        b-col.p-0.text-center.position-relative#game( cols="12" )
            b-col.mx-auto.p-0( cols="12" )
                b-row.m-0.p-0.position-relative
                    b-col.mx-auto.p-0.text-center( cols="10" )
                        img.img-fluid( src="@/assets/images/game.svg" alt="Naturella Game" )
                    b-col.mx-auto.p-0.pt-4.text-center( cols="10" )
                        p.h5.text-white 11 мая 2020 года в 12.00&nbsp;
                        p.h5.text-white по адресу: г. Минск, пер. Козлова, 25, пом.22
                        p.text-white С полными правилами рекламной игры можно ознакомиться
                            router-link.text-white( to="/rules" target="_blank") &nbsp;здесь
        b-col.p-0.text-center.position-relative( cols="12" )
            b-col.mx-auto.p-0( cols="12" )
                b-row.m-0.p-0.position-relative
                    b-col.mx-auto.p-0.text-right( cols="5" )
                        img.img-fluid( src="@/assets/images/flower.png" alt="Naturella Game" )
                    b-col.mx-auto.pl-5( cols="7" )
                        b-row.p-0.m-0
                            b-col( cols="12" )
                                span.phone.icon( @click="callTo" )
                                    font-awesome-icon( :icon="['fas', 'phone']" size="2x" color="#fff" style="transform: rotate(90deg)")
                            b-col.text-left( cols="12" )
                                span.call.text-white.h5.font-weight-bold( @click="callTo" style="margin-left: -5%" ) +375 29 608 19 49
                    b-col.p-0.text-center.position-relative( cols="12" )
                        b-col.mx-auto.p-0( cols="12" )
                            b-row.m-0.p-0.position-relative
                                b-col.mx-auto.p-0.text-center( cols="10" )
                                    img.img-fluid( src="@/assets/images/description.png" alt="Naturella Description" )


</template>

<script>
    import { isMobile } from 'mobile-device-detect';
    export default {
        data() {
            return {
                mobile: isMobile,
            }
        },
        methods: {
            callTo() {
                window.open('tel:+375296081949', '_self')
            }

        }
    }
</script>
