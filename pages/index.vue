import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'

<template>
  <div>
    <svg-symbols></svg-symbols>
    <vHeader></vHeader>
    <div class="my-6 p-4 rounded bg-gray-200 border w-1/3 text-center mx-auto">
      <h1 class="text-2xl">Localfarm - Basel Hack 2021</h1>
    </div>
  </div>
</template>

<script>

export default {
  components: { VHeader, svgSymbols },
  methods: {
    async fetchMockApi () {
      await this.$axios.get(process.env.baseUrl)
        .then(response => console.log(response))
        .catch(error => console.error(error))
    }
  }
}
</script>
