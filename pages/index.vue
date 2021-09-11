<template>
  <div>
    <svg-symbols />
    <vHeader />
    <teaser :farms="farms" />
    <NavBar />
  </div>
</template>

<script>
import VHeader from '~/components/vHeader.vue'
import svgSymbols from '~/components/svgSymbols.vue'
import teaser from '~/components/teaser.vue'
import NavBar from '~/components/NavBar.vue'

export default {
    components: { VHeader, svgSymbols, teaser, NavBar },
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
            await this.$axios.get(process.env.baseUrl)
            .then(res => {
                result = res.data
                console.log(res);
            })
            .catch(error => {
                console.error(error)
            })
            return result
        }
    }
}
</script>
