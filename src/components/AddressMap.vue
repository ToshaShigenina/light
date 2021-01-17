<template>
  <div ref="googleMap" id="map"></div>
</template>

<script>
import GoogleMapsApiLoader from 'google-maps-api-loader'

export default {
  name: 'AddressMap',
  props: {
    coords: Object
  },
  data () {
    return {
      apiKey: 'AIzaSyDit99wUrDjefbHYSg7KMK0GL4iWYeG5Ik',
      mapOptions: {
        zoom: 4,
        center: this.coords
      },
      google: null,
      map: null
    }
  },
  methods: {
    initializeMap () {
      const mapContainer = this.$refs.googleMap
      this.map = new this.google.maps.Map(
        mapContainer, this.mapOptions
      )
    }
  },
  async mounted () {
    const googleMapApi = await GoogleMapsApiLoader({
      apiKey: this.apiKey
    })

    this.google = googleMapApi
    this.initializeMap()
  }
}

</script>

<style scoped lang="sass">
#map
  width: 100%
  height: 400px
</style>
