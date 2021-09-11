<template>
  <li class="text-center">
        <div @click="$emit('clicked', obj.text)">
              <div>
                <svg 
                    class="mx-auto"
                    width="25"
                    height="25"
                    viewBox="0 0 25 25"
                    preserveAspectRatio="xMinYMax"
                >
                    <use v-bind:xlink:href="svgHref"></use>
                </svg>
              </div>
              <p class="mt-1 text-xs">{{ obj.text }}</p>
        </div>
  </li>
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
        }
    }
}
</script>

<style>

</style>