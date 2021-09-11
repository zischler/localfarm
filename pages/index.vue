<template>
  <div>
    <svg-symbols></svg-symbols>
    <vHeader></vHeader>
    <div class="my-6 p-4 rounded bg-gray-200 border w-1/3 text-center mx-auto">
      <h1 class="text-2xl">Localfarm - Basel Hack 2021</h1>
    </div>
    <google-map :center="{lat: 47.5410808,lng: 7.5938071}" :markers="[{position:{lat: 47.5410808,lng: 7.5938071}, title: 'test'}]"></google-map>
  </div>
</template>

<script>
import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'
import googleMap from '~/components/googleMap.vue'

export default {
  components: { VHeader, svgSymbols, googleMap },
  methods: {
    async fetchMockApi () {
      await this.$axios.get(process.env.baseUrl)
        .then(response => console.log(response))
        .catch(error => console.error(error))
    }
  }
}
</script>
