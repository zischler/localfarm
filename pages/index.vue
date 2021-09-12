<template>
  <div>
<<<<<<< Updated upstream
    <div class="my-6 p-4 rounded bg-gray-200 border w-1/3 text-center mx-auto">
      <h1 class="text-2xl">Localfarm - Basel Hack 2021</h1>
    </div>
    <google-map :center="{lat: 47.5410808,lng: 7.5938071}" :markers="[{position:{lat: 47.5410808,lng: 7.5938071}, title: 'test'}]"></google-map>
    <FarmCard :farms="farms" />
=======
    <svg-symbols />
    <vHeader />
            <SearchFilter />

    <teaser :farms="farms" />
    <NavBar />
>>>>>>> Stashed changes
  </div>
</template>

<script>
import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'
<<<<<<< Updated upstream
import googleMap from '~/components/googleMap.vue'
import FarmCard from '~/components/FarmCard.vue'

export default {
  components: { VHeader, svgSymbols, googleMap, FarmCard },
  data() {
      return {
          farms: []
      }
  },
  async mounted () {
      this.farms = await this.fetchMockApi()
  },
  methods: {
        async fetchMockApi () {
            let result = []
=======
import teaser from '~/components/teaser.vue'
import NavBar from '~/components/NavBar.vue'
import SearchFilter from '~/components/SearchFilter.vue'
export default {
    components: { VHeader, svgSymbols, teaser, NavBar, SearchFilter },
    data() {
        return {
            farms: {}
        }
    },
    async mounted () {
        this.farms = await this.fetchFarmsData()
    },
    methods: {
        async fetchFarmsData () {
            let result = {}
>>>>>>> Stashed changes
            await this.$axios.get(process.env.baseUrl)
            .then(response => {
                result = response.data
            })
            .catch(error => {
                console.error(error)
            })
            return result
        }
    }
}
</script>
