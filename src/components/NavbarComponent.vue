<template lang="pug">
    b-navbar.position-fixed.fixed-top.m-0.rounded-0( toggleable="lg" type="dark" variant="warning" )
        b-navbar-brand
            router-link.nav-link.text-dark.font-weight-bold( to="/" ) Naturella
        b-navbar-toggle( target="nav" )
        b-collapse#nav( is-nav )
            b-navbar-nav
                b-nav-item.text-white( @click="$router.push({name: 'admin.export'}).catch(err => {})") Выгрузить участников
                b-nav-item.text-white( @click="$router.push({name: 'admin.results'}).catch(err => {})" ) Добавить результаты
                b-nav-item.text-white( @click="$router.push({name: 'admin.register'}).catch(err => {})" ) Добавить участника
                b-nav-item.text-white( @click="$router.push({name: 'admin'}).catch(err => {})" )( v-if="$route.name !== 'admin'" ) Панель администратора
            b-navbar-nav.ml-auto
                b-nav-item.text-white( @click="logout()" ) Выйти
</template>

<script>
    export default {
        methods: {
            logout() {
                this.$jwt.remove();
                this.$router.push({name: 'login'})
            }
        }
    }
</script>
