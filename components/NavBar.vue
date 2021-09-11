<template>
    <div class="fixed bottom-0 bg-white w-full">
        <ul class="grid grid-cols-4 gap-2 p-2 max-w-5xl mx-auto">
            <li is="NavItem" name="Entdecken" path="/" svg="entdecken"></li>
            <li is="NavItem" name="Karte" path="/map" svg="karte"></li>
            <li is="NavItem" name="Favoriten" path="/favorites" svg="favoriten"></li>
            <li is="NavItem" name="Infos" path="/info" svg="infos"></li>
        </ul>
    </div>
</template>

<script>
// import NavItem from '~/components/NavItem.vue'
export default {
    // components: { NavItem },
    computed: {
        routes: function () {
            return this.$router.getRoutes()
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
