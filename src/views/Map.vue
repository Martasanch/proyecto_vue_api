<template>
  <div class="map">
   <h1>estoy en Map</h1>
   <div id="mapid"></div>
  </div>
</template>

<script>
// la librería leaftet la instalamos de npm: vue2-leaflet

import L from "leaflet"
import {onMounted} from "vue"
export default {
setup(){
let mymap

//con onMounted creará el mapa  cuando la vista está cargada, si no vue siempre ejecuta el setup antes de que se cargue la vista
onMounted(()=>{
    mymap = L.map('mapid').setView([40.40254656600095, -3.7461006070340663], 13) //pongo las coordenadas de mi zona (las copio de google map)
    L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
        attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
        maxZoom: 18,
        id: 'mapbox/streets-v11',
        tileSize: 512,
        zoomOffset: -1,
        accessToken: 'your.mapbox.access.token'
    }).addTo(mymap)

})

  return{}
}
} 
</script>





<style lang="scss" scoped>
#mapid { height: 500px; }
</style>