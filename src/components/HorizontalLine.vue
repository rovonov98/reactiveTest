<template>
  <div class="line">
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.line {
  margin: 0 auto 2.2rem auto;
  width: $whole-content-width;
  @media(max-width: 576px) {
    max-width: $whole-content-width-mobile;
  }
  border-top: 1px solid $dark-grey;
  opacity: 0.3;
}
</style>