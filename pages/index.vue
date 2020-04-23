<template>
 <div>
    <Logo @addEd='meto2'></Logo>
    <div id="map-wrap" style="height: 70vh" v-if="unshow">
 <no-ssr>
   <l-map :zoom=11 :center="[this.postList,this.postList1]">
     <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"></l-tile-layer>
     <l-marker :lat-lng="[this.postList,this.postList1]"></l-marker>
   </l-map>
 </no-ssr>
</div>
          
 </div>
</template>

<script>
// import L from 'nuxt-leaflet';
import Logo from '~/components/Logo.vue'

export default {
  data () {
    return {
      postList: '0',
      postList1: '0',
      unshow: false
    }
  },
  components: {
    Logo,
  },
  methods: {
    meto2(searchKey) {
      this.unshow = true
      var url0 = 'https://nominatim.openstreetmap.org/search?format=json&countrycodes=IN&q='     
      var url= url0 + searchKey;
      fetch(url)
      .then(res => res.json())
      .then(data => {
        this.postList = data[0].lat;
        this.postList1 = data[0].lon;
      //   var mymap = L.map('mapid').setView([this.postList, this.postList1], 11);
      // // var mymap = L.map('mapid').setView([12.9791198, 77.5912997], 11);
      // var attribution = 
      //   '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreerMap</a> contributor';
      // const tileUrl = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png';
      // const tiles = L.tileLayer(tileUrl, { attribution });
      // tiles.addTo(mymap);
      })
    }
}
}
</script>
