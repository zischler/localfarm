<template>
    <div>
        <svg-symbols />
        <div class="max-w-5xl w-full h-full mx-auto px-4 pb-12">
            <FarmCard v-for="farm in farms" :farm="farm" :key="farm.id" />
        </div>
    </div>
</template>

<script>
// import FarmCard from '~/components/FarmCard.vue'

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
