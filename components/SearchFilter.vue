<template>
    <div class="relative max-w-5xl w-full h-full mx-auto px-4 mt-4">
        <button
            @click="isActive = !isActive"
        >
            <svg
                width="45"
                height="40"
                viewBox="0 0 45 40"
                preserveAspectRatio="xMinYMax"
                v-if="!isActive"
            >
                <use xlink:href="#sliders"></use>
            </svg>
            <svg
                width="45"
                height="40"
                viewBox="0 0 45 40"
                preserveAspectRatio="xMinYMax"
                v-if="isActive"
            >
                <use xlink:href="#sliders-active"></use>
            </svg>
        </button>
           <input v-model="searchValue" @input="log" class="absolute mt-2 ml-4 focus:outline-none" v-if="isActiveSearch" type="text" id="name" name="name"
       size="10" v-on:keyup="searchValue = $event.target.value">
        <button
            @click="isActiveSearch = !isActiveSearch"
        >
            <svg
                width="45"
                height="40"
                viewBox="0 0 45 40"
                preserveAspectRatio="xMinYMax"
                v-if="!isActiveSearch"
            >
                <use xlink:href="#search"></use>
            </svg>
            <svg
                width="250"
                height="40"
                viewBox="0 0 250 40"
                preserveAspectRatio="xMinYMax"
                v-if="isActiveSearch"
            >
                <use xlink:href="#search-active"></use>
            </svg>
        </button>
     
        <div
        v-if="isActive"
            class="w-full absolute z-50 bg-white max-w-xs h-mx mx-4 p-4 border-2 rounded-md border-f-green"
            style="background-color:white"
        >
            <select @input="log" class="dropdown w-full px-6 py-2" name="location" id="location" v-model="location">
                <option value="">Orte auswählen</option>
                <option value="Liestal">Liestal</option>
                <option value="Laufen">Laufen</option>
                <option value="Reinach">Reinach</option>
                <option value="Müchenstein">Müchenstein</option>
                <option value="Muttenz">Muttenz</option>
                <option value="Bottmingen">Bottmingen</option>
                <option value="Seewen">Seewen</option>
                <option value="Ziefen">Ziefen</option>
                <option value="Binningen">Binningen</option>
                <option value="Oberwil">Oberwil</option>
                <option value="Allschwil">Allschwil</option>
                <option value="Therwil">Therwil</option>
                <option value="Aesch">Aesch</option>
            </select>

            <p class="mt-4 mb-2">Erreichbarkeit</p>
            <div class="flex">
                <small>Wandern</small>
                <svg
                    class="mx-2"
                    width="25"
                    height="20"
                    viewBox="0 0 25 20"
                    preserveAspectRatio="xMinYMax"
                >
                    <use xlink:href="#walk"></use>
                </svg>
                <input @change="log" type="checkbox" id="walk" name="walk" v-model="walk" />
            </div>
            <div class="flex">
                <small>Fahrzeug</small>
                <svg
                    class="mx-2"
                    width="25"
                    height="20"
                    viewBox="0 0 25 20"
                    preserveAspectRatio="xMinYMax"
                >
                    <use xlink:href="#car"></use>
                </svg>
                <input @change="log" type="checkbox" id="car" name="car" v-model="car"/>
            </div>

            <div class="flex">
                <small>Fahrrad</small>
                <svg
                    class="mx-2"
                    width="25"
                    height="20"
                    viewBox="0 0 25 20"
                    preserveAspectRatio="xMinYMax"
                >
                    <use xlink:href="#bicycle"></use>
                </svg>
                <input @change="log" type="checkbox" id="bicycle" name="bicycle"  v-model="bicycle"/>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return { 
            isActive: false,
            isActiveSearch: false,
            searchValue: "",
            walk: false,
            car: false,
            bicycle: false,
            location: ""
        };
    },
    props: ['farms'],
    methods: {
        log(event) {
            let filterBy = (farm) => {
                if (this.car == true) return farm.reachability === "car"
                if (this.bicycle == true) return farm.reachability === "bicycle"
                if (this.walk == true) return farm.reachability === "walk"
            }
            let result = this.farms.filter(farm => filterBy(farm) )
        
            this.$emit('result', result)
            
        }
    }
};

</script>

<style scoped>
.dropdown {
    background-image: url(../static/dropdown.svg);
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
