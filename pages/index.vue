<template>
  <div>
    <svg-symbols></svg-symbols>
    <vHeader></vHeader>
    <div class="my-6 p-4 rounded bg-gray-200 border w-1/3 text-center mx-auto">
      <h1 class="text-2xl">Localfarm - Basel Hack 2021</h1>
    </div>
    <NavBar></NavBar>
  </div>
</template>

<script>
import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'
import NavBar from '~/components/NavBar.vue'

export default {
  components: { VHeader, svgSymbols, NavBar },
  data() {
    return {
      farmData: {}
    }
  },
  async mounted () {
    this.farmData = await this.fetchMockApi()
  },
  methods: {
    async fetchMockApi () {
      let result = {}
      await this.$axios.get(process.env.baseUrl)
        .then(response => result = response)
        .catch(error => console.error(error))
      return result
    }
  }
}
</script>
