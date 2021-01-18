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
      position: this.coords,
      google: null,
      map: null,
      marker: null
    }
  },
  methods: {
    initializeMap () {
      const mapContainer = this.$refs.googleMap
      this.map = new this.google.maps.Map(
        mapContainer, {
          zoom: 18,
          center: this.position
        }
      )
      this.marker = new this.google.maps.Marker({
        position: this.position,
        map: this.map
      })
    },
    async loadMap () {
      const googleMapApi = await GoogleMapsApiLoader({
        apiKey: this.apiKey
      })

      this.google = googleMapApi
      this.initializeMap()
    }
  },
  watch: {
    position: {
      handler: function (newVal, oldVal) {
        this.initializeMap()
      },
      deep: true
    }
  },
  async mounted () {
    this.loadMap()
  }
}

</script>

<style scoped lang="sass">
#map
  width: 100%
  height: 400px
</style>
