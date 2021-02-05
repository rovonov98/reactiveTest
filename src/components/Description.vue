<template>
  <section class="description">
    <h1 class="description__title">Выдача градостроительного плана земельного участка</h1>
    <div class="side-content">
      <img  class="eagle-logo" src="./../assets/img/Eagle.svg" alt="Eagle">
      <span class="side-content__bold-text">Услугу предоставляет</span>
      <span class="side-content__text">Орган местного самоуправления</span>
    </div>
  </section>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.description {
  padding-top: 4rem;
  max-width: $whole-content-width;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}
.description__title {
  max-width: $main-content-width;
  @include responsive-font(48, 15);
}
.side-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  @include responsive-font(14, 8);
}
.eagle-logo {
  max-width: 3rem;
}
</style>