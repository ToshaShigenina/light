<template>
  <div ref="googleMap" id="map"></div>
</template>

<script>
export default {
  name: 'AddressMap',
  props: {
    coords: Object
  },
  data () {
    return {
      mapOptions: {
        zoom: 4,
        center: this.coords
      }
    }
  },
  methods: {
    initMap () {
      const map = new google.maps.Map(this.$refs.googleMap, this.mapOptions)
      const marker = new google.maps.Marker({
        position: this.coords,
        map: map
      })
    }
  },
  mounted () {
    this.initMap()
  }
}

</script>

<style scoped lang="sass">
#map
  width: 100%
  height: 400px
</style>
