<template>
<div id="parent">
    <LoginRegisterPage @set-login="setLogin" v-show="!isLogin"></LoginRegisterPage>
    <HomePage @set-logout="setLogout" v-if="isLogin"></HomePage>
</div>
</template>

<script>
import LoginRegisterPage from '../src/views/LoginRegisterPage'
import HomePage from "../src/views/HomePage";

export default {
    data() {
        return {
            isLogin: false
        }
    },
    components:{
        LoginRegisterPage,
        HomePage
    },
    methods: {
        setLogin() {
            this.isLogin = true
            
        },
        setLogout() {
            this.isLogin = false
        }
    },
    created() {
        if(localStorage.getItem('token')) {
            this.isLogin = true
        } else {
            this.isLogin = false
        }
    }
}

</script>


<style>

</style>