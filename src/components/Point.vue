<template>
  <li class="point__item">
    <input
      :id="'address' + index"
      :checked="index === 0"
      @change="changeAddress(index)"
      name="address"
      type="radio"
      class="point__radio">
    <label
      :for="'address' + index"
      class="point__label">
      <span class="address">{{ address }}</span>
      <ul class="prop">
        <li
          class="prop__item"
          v-for="(budget, i) in budgets"
          :key="i">{{ budget }}</li>
      </ul>
    </label>
  </li>
</template>

<script>
export default {
  name: 'Point',
  props: {
    point: Object,
    index: Number
  },
  data () {
    return {
      address: this.point.address,
      budgets: this.point.budgets
    }
  },
  methods: {
    changeAddress (i) {
      this.$emit('change-element', i)
    }
  }
}

</script>

<style lang="sass">

</style>
