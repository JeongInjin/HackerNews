<template>
    <div>
        <user-profile :info="userInfo">
            <div slot="username">{{userInfo.id}}</div>
            <template slot="time">{{userInfo.created}}</template>
            <div slot="karma">{{userInfo.karma}}</div>
        </user-profile>
        <!--        <p>name : {{userInfo.id}}</p>-->
        <!--        <p>karma : {{userInfo.karma}}</p>-->
        <!--        <p>created : {{userInfo.created}}</p>-->
    </div>
</template>

<script>
    import UserProfile from "../components/UserProfile";

    export default {
        components: {
            UserProfile,
        },
        computed: {
            userInfo() {
                return this.$store.state.user;
            }
        },
        created() {
            const userName = this.$route.params.id;
            this.$store.dispatch('FETCH_USER', userName);
        },

    }
</script>

<style scoped>

</style>