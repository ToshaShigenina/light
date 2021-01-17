<template>
  <section class="wrapper">
    <div class="wrapper__item">
      <ul class="point" v-if="loader">
        <point
          v-for="(point, i) in pickPoints"
          :key="'address' + i"
          :index="i"
          :point="point"
          @change-element="selectElement"
          ></point>
      </ul>
    </div>
    <div class="wrapper__item">
      <address-map :coords="coords"></address-map>
    </div>
  </section>
</template>

<script>
import AddressMap from './AddressMap.vue'
import Point from './Point.vue'

export default {
  name: 'Address',
  data () {
    return {
      pickPoints: [],
      loader: false,
      index: 0,
      coords: {
        lat: null,
        lng: null
      }
    }
  },
  components: {
    AddressMap,
    Point
  },
  methods: {
    selectElement (i) {
      this.index = i
      this.coords.lat = this.pickPoints[this.index].latitude
      this.coords.lng = this.pickPoints[this.index].longitude
    }
  },
  created () {
    fetch('https://express-shina.ru/vacancy/geo-state')
      .then(async response => {
        const data = await response.json()
        this.pickPoints = data.pickPoints
      })
      .then(() => {
        this.loader = true
        this.coords.lat = this.pickPoints[this.index].latitude
        this.coords.lng = this.pickPoints[this.index].longitude
      })
      .catch((error) => {
        console.error(error.message)
      })
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
