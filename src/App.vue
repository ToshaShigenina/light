<template>
  <div id="app">
    <Address></Address>
  </div>
</template>

<script>
import Address from './components/Address.vue'

export default {
  name: 'App',
  components: {
    Address
  }
}

</script>

<style lang="sass">
$font: 'Arial', sans-serif
$color-main-bg: #2a2c2d
$color-address-bg: #3a3d3e
$color-prop-bg: #282c2d
$color-light-text: #969c9f
$color-prop-active-bg: #404749
$font-size: 16px

*
  margin: 0
  padding: 0
  box-sizing: border-box

html,
body
  width: 100%
  min-height: 100vh
  height: auto

body
  background-color: $color-main-bg
  color: $color-light-text
  line-height: 1
  font-size: $font-size
  font-family: $font

.wrapper
  display: flex
  flex-direction: column
  width: 100%
  max-width: 1024px
  margin: 0 auto
  padding: 14px 8px
  &__item
    width: 100%
    &:last-child
      margin-top: 14px

.point
  list-style-type: none
  &__item
    margin-top: 10px
    &:first-child
      margin-top: 0
  &__label
    display: block
    padding: 10px 14px
    background-color: $color-address-bg
  &__radio
    display: none
    &:checked + .point__label
      transition: background-color .5s
      background-color: $color-prop-active-bg

.prop
  list-style-type: none
  display: flex
  margin-top: 14px
  &__item
    margin-right: 12px
    padding: 8px 12px
    font-size: 70%
    background-color: $color-prop-bg

@media (screen and min-width: 768px)
  .wrapper
    flex-direction: row
    &__item
      flex-basis: 50%
      &:last-child
        margin-top: 0
        margin-left: 14px
</style>
