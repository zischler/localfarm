<template>
    <ul class="grid grid-cols-4 gap-2">
        <li is="NavItem" v-for="obj,index of objs" :key="obj.text" :obj="obj" @clicked="changeToActive($event, index)"></li>
    </ul>
</template>

<script>
import NavItem from '~/components/NavItem.vue'
export default {
    components: {NavItem},
    data () {
        return {
            objs: [
                {
                    text: "Entdecken",
                    path: '/',
                    svg: 'compass',
                    active: true
                },
                {
                    text: "Karte",
                    path: '/map',
                    svg: 'map',
                    active: false
                },
                {
                    text: "Favoriten",
                    path: '/favorites',
                    svg: 'heart',
                    active: false
                },
                {
                    text: "Infos",
                    path: '/info',
                    svg: 'house',
                    active: false
                }
            ]
        }
    },
    methods: {
        changeToActive (event, index) {
            let obj = this.objs[index]
            let objs = this.objs.filter(elem => elem != obj)
            for(let i=0; i<objs.length; i++) {
                let objInFor = objs[i]
                objInFor.active = false
            }
            if(obj.text === event){
                obj.active = true
            } else {
                obj.active = false
            }
        }
    }
}
</script>

<style>
</style>
