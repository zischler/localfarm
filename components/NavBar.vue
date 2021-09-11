<template>
    <div class="fixed bottom-0 bg-white w-full">
        <ul class="grid grid-cols-4 gap-2 p-2 max-w-5xl mx-auto">
            <li is="NavItem" v-for="route in routes" :key="route.name" :item="route"></li>
        </ul>
    </div>
</template>

<script>
// import NavItem from '~/components/NavItem.vue'
export default {
    // components: { NavItem },
    computed: {
        routes: function () {
            const result = this.$router.getRoutes()
            console.log(result)
            return result
        }
        // routes () {
        //     return this.$router.getRoutes()
        // }
    },
    mounted () {
        console.log(this.$route)
    }
}
</script>

<style>
</style>
