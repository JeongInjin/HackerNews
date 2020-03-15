<template>
    <div>
        <div v-for="job in this.$store.state.jobs">{{ job.title }}</div>
    </div>
</template>

<script>
    import {feachJobsList} from '../api/index'

    export default {
        created() {
            this.$store.dispatch('FETCH_JOBS');
        }
    }


</script>

<style scoped>

</style>