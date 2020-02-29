<template lang="pug">
    b-navbar.always_navbar.bg-transparent( toggleable="lg" type="dark" variant="info" )
        b-navbar-brand.text-center.mx-auto.w-100( v-if="mobile" @click="$router.push({name: 'main'}).catch(() => {})")
            img.img-fluid( v-if="!mobile" src="@/assets/images/logo.png" )
        b-button#toggler.bg-transparent.border-0( v-if="mobile" @click="onClick" target="nav-collapse" :style="mobile ? 'position: absolute; top: 20px; right: 6px; z-index: 5' : ''")
            font-awesome-icon.text-white( v-if="!isToggled" transform size="lg" :icon="['fas', 'bars']" )
            font-awesome-icon.text-white( v-else size="lg" :icon="['fas', 'times']" )
        b-collapse#nav-collapse( is-nav )
            b-navbar-nav.mx-auto.always_navbar_nav.d-flex.text-white( :style="style" )
                b-nav-item( v-if="!mobile" @click="$router.push({name: 'main'}).catch(() => {})" )
                    img.img-fluid( src="@/assets/images/logo.png" )
                b-nav-item.text-uppercase.text-white.mx-auto.my-4.font-weight-bold( v-for="(item, i) in $store.getters.menu"
                    :key="i" @click="scrollTo(item.anchor)"  style="z-index: 1") {{ item.title }}
                b-nav-item.text-uppercase.text-white.mx-auto.my-4.font-weight-bold.resultri(
                    @click="$router.push({name: 'previous'}).catch(() => {}); isToggled = !isToggled; $root.$emit('bv::toggle::collapse',target)"
                    ) Результаты РИ always

</template>

<script>
    import { isMobile } from "mobile-device-detect";
    export default {
        data() {
            return {
                mobile: isMobile,
                style: null,
                isToggled: false,
                target: 'nav-collapse'
            }
        },
        mounted() {
            this.style = this.mobile ? 'height: 100vh; width: 100vw; position: fixed; top: 0; left: 0; z-index: 4; background: rgb(62,178,27);\n' +
                'background: -moz-linear-gradient(180deg, rgba(62,178,27,1) 0%, rgba(91,218,53,1) 50%, rgba(96,223,58,1) 100%);\n' +
                'background: -webkit-linear-gradient(180deg, rgba(62,178,27,1) 0%, rgba(91,218,53,1) 50%, rgba(96,223,58,1) 100%);\n' +
                'background: linear-gradient(180deg, rgba(62,178,27,1) 0%, rgba(91,218,53,1) 50%, rgba(96,223,58,1) 100%);\n' +
                'filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#3eb21b",endColorstr="#60df3a",GradientType=1);' : '';
        },
        methods: {
            onClick(evt) {
                this.$emit('click', evt);
                if (!evt.defaultPrevented) {
                    this.isToggled = !this.isToggled;
                    this.$root.$emit('bv::toggle::collapse', this.target)
                }
            },
            scrollTo(element) {
                if(this.$route.name.includes('main')) {
                    this.$scrollTo(element);
                    if(this.mobile && this.isToggled)  {
                        this.isToggled = !this.isToggled;
                        this.$root.$emit('bv::toggle::collapse', this.target)
                    }
                } else {
                    this.$router.push({name: 'main'});
                    if(this.mobile && this.isToggled)  {
                        this.isToggled = !this.isToggled;
                        this.$root.$emit('bv::toggle::collapse', this.target)
                    }
                }
            }
        }
    }
</script>

<style scoped>
    .resultri {
        background: linear-gradient(106.26deg, #7F41C1 3.05%, #9454D9 27.48%, #AE75EC 50.72%, #9454D9 70.48%, #7F41C1 97.9%);
        border-radius: 50px;
        box-shadow: 3px 6px 10px rgba(61, 22, 115, 0.2);
        height: 3rem;
        width: 17rem;
        margin-top: 2.3rem!important;
    }
    a {
        color: white!important;
    }
    a:hover {
        color: rgb(190, 243, 174)!important;
    }
</style>
