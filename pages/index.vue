<template>
    <div>
        <div class="max-w-5xl w-full h-full mx-auto px-4 pb-12">
            <SearchFilter :farms="farms" @result="changeFarms"/>
            <FarmCard v-for="farm in farms" :farm="farm" :key="farm.id" />
        </div>
    </div>
</template>

<script>
// import FarmCard from '~/components/FarmCard.vue'
export default {
    data() {
        return {
            farms: [],
            oldFarms: []
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
        },
        changeFarms(event){
            this.oldFarms = this.farms
            if(event.length > 0) {
                this.farms = event
            } else {
                this.farms = this.oldFarms
            }
        }
    }
}
</script>