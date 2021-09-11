<template>
    <NuxtLink :to="obj.path" class="text-center">
        <div>
            <svg class="mx-auto" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                <use v-bind:xlink:href="svgHref"></use>
            </svg>
        </div>
        <div @click="$emit('clicked', obj.text)">
            <p :style="pStyle" class="mt-1 text-xs">{{ obj.text }}</p>  
        </div>
    </NuxtLink>
</template>

<script>
export default {
    props: ['obj'],
    computed: {
        svgHref() {
            let svg = "#" + this.obj.svg
            if(this.obj.active) {
                svg = svg + "-active"
            }
            return svg
        },
        pStyle() {
            if(this.obj.active) {
                return {color: '#FF5470'}
            } else {
                return {color: '#000000'}
            }
        }
    }
}
</script>

<style>

</style>