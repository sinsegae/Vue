<template>
    <div id="app">
        <router-view></router-view>
        <router-link to="/board" v-show="this.$route.path !== '/board'">게시판</router-link>
        <router-link to="/" v-show="this.$route.path !== '/'">홈으로</router-link>
    </div>
</template>

<script>

export default {
    
}
</script>