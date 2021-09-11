<template>
  <div>
    <svg-symbols></svg-symbols>
    <vHeader></vHeader>
    <div>
      <FarmCard v-if="currentView == 'Entdecken'" :farms="farms"></FarmCard>
    </div>
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
      farms: []
    }
  },
  async mounted () {
    this.farms = await this.fetchMockApi()
  },
  methods: {
    async fetchMockApi () {
      let result = {}
      await this.$axios.get(process.env.baseUrl)
        .then(response => result = response.data)
        .catch(error => console.error(error))
      return result
    },
    changeView(event) {
      this.currentView = event
    }
  }
}
</script>
