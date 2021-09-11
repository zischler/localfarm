<template>
    <NuxtLink :to="obj.path" class="text-center">
        <div>
            <svg class="mx-auto fill-current" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                <use v-bind:xlink:href="'#' + obj.svg"></use>
            </svg>
        </div>
        <div>
            <p class="mt-1 text-xs">{{ obj.text }}</p>
        </div>
    </NuxtLink>
</template>

<script>
export default {
    props: ['obj'],
}
</script>

<style>

</style>