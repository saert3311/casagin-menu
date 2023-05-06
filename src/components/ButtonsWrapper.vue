<template>
  <div class="column" v-for="item in menus.items">
    <a :href="getAssetLink(item.fields.archivo.sys.id)">
        <button class="button is-medium is-fullwidth is-outlined is-rounded">{{item.fields.nombre}}</button>
    </a>
  </div>
</template>
<script>
import axios from 'axios'
export default {
    data(){
        return {
            menus:[]
        }
    },
    methods:{
        fetchItems(){
            axios
            .get(`https://cdn.contentful.com/spaces/${import.meta.env.VITE_SPACE_ID}/environments/master/entries?access_token=${import.meta.env.VITE_ACCESS_TOKEN}`)
            .then(res => {
                this.menus = res.data
            })
            .catch(err => {
                console.log(error.response.data);
                alert('Ha ocurrido un error obteniendo los menus recarga la pagina')
            })
        },
        getAssetLink(id){
            const filtered = this.menus.includes.Asset.filter(item => item.sys.id == id)
            console.log(filtered)
            return filtered[0].fields.file.url
        }
    },
    mounted(){
        this.fetchItems()
    }
}
</script>
<style>
    
</style>