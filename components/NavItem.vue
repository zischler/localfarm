<template>
    <NuxtLink :class="{ 'text-red-500': activeClass }" :to="path" class="text-center">
        <div>
            <svg class="mx-auto fill-current stroke-current text-blue-500" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                <use v-bind:xlink:href="'#' + svgId"></use>
            </svg>
        </div>
        <div>
            <p class="mt-1 text-xs">{{ name }}</p>
        </div>
    </NuxtLink>
</template>

<script>
export default {
    computed: {
        activeClass () {
            if (this.$route.path === this.path) {
                return true
            }
            return false
        },
        svgId () {
            if (this.activeClass) {
                return this.svg + "-active"
            } 
            return this.svg
        }
    },
    props: {
        name: String,
        path: String,
        svg: String
    }
}
</script>

<style>

</style>