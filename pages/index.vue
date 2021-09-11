<template>
  <div>
    <svg-symbols></svg-symbols>
    <FarmCard :farms="farms" />
  </div>
</template>

<script>
import FarmCard from '~/components/FarmCard.vue'

export default {
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
