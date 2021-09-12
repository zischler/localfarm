<template>
    <div class="fixed bottom-0 bg-white w-full">
        <ul class="grid grid-cols-4 gap-2 p-2 max-w-5xl mx-auto">
            <li is="NavItem" v-for="obj, index of objs" :key="obj.text" :obj="obj"></li>
        </ul>
    </div>
</template>

<script>
import NavItem from '~/components/NavItem.vue'
export default {
    components: { NavItem },
    data () {
        return {
            objs: [
                {
                    text: "Entdecken",
                    path: '/',
                    svg: 'compass'
                },
                {
                    text: "Karte",
                    path: '/map',
                    svg: 'map'
                },
                {
                    text: "Favoriten",
                    path: '/favorites',
                    svg: 'heart'
                },
                {
                    text: "Infos",
                    path: '/info',
                    svg: 'house'
                }
            ]
        }
    },
    methods: {
        
    }
}
</script>

<style>
</style>
