<template>
  <div>
        <div class="max-w-5xl w-full h-full mx-auto px-4 pb-12">
            <div v-show="farms.length > 0" class="my-4">
              <FarmCard v-for="farm in farms" :farm="farm" :key="farm.id" />
            </div>
            <div v-show="farms.length < 1" class="py-4 rounded-full px-12 border my-8 bg-red-400 border border-red-500">
              <h2 class="text-2xl text-white">Keine Favoriten vorhanden</h2>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      favoritesList: [],
      farms: [],
      oldFarms: []
    }
  },
 async mounted() {
    this.loadLocalStorage()
    this.oldFarms = await this.fetchMockApi()
    let list1 = []
    this.oldFarms.forEach(obj => {
      list1.push(obj.id)
    })
    let list2 = []
    this.favoritesList.forEach(i => {
      this.oldFarms.forEach(b => {
        if(i == b.id) {
          list2.push(b)
        }
      })
    })
    this.farms = list2
  },
  methods: {
    loadLocalStorage() {
            let storage = JSON.parse(localStorage.getItem('favorites'))
            if(storage) {
                this.favoritesList = storage
            } else {
                let emptyList = JSON.stringify([])
                localStorage.setItem('favorites', emptyList)
                this.favoritesList = JSON.parse(emptyList)
            }
            
        },
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