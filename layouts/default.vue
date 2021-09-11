<template>
  <div>
    <vHeader></vHeader>
    <Nuxt />
    <NavBar @view="changeView"></NavBar>
  </div>
</template>

<script>
import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'
import NavBar from '~/components/NavBar.vue'
import FarmCard from '~/components/FarmCard.vue'

export default {
    components: { VHeader, svgSymbols, NavBar, FarmCard },
    data() {
        return {
            currentView: 'Entdecken',
        }
    },
    methods: {
        changeView(event) {
            this.currentView = event
        }
    }
}
</script>