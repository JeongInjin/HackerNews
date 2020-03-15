<template>
    <div>
        <ul class="news-list">
            <li v-for="item in this.fetchedAsk" class="post">
                <div class="points">
                    {{item.points}}
                </div>
                <div>
                    <p class="news-title">
                        <router-link v-bind:to="`item/${item.id}`">
                            {{item.title}}
                        </router-link>
                    </p>
                    <small class="link-text">
                        {{item.time_ago}} by
                        <router-link class="link-text" v-bind:to="`user/${item.user}`">{{item.user}}</router-link>
                    </small>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    import {mapState, mapGetters} from 'vuex'

    export default {
        computed: {
            ...mapGetters([
                'fetchedAsk'
            ])

            // ...mapGetters({
            //     fetchedAsk :'fetchedAsk'
            // })

            // ...mapState({
            //     ask: state => state.ask
            // })
        },
        created() {
            this.$store.dispatch('FETCH_ASK');
        }
    }

</script>

<style scoped>
    .news-list {
        margin: 0px;
        padding: 0px;
    }

    .post {
        list-style: none;
        display: flex;
        align-items: center;
        border-bottom: 1px solid #eee;
    }

    .points {
        width: 80px;
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #42b883;
    }

    .news-title {
        margin: 0px;
    }

    .link-text {
        color: #828282;
    }
</style>