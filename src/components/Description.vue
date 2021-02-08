<template>
  <section class="description">
    <div class="description__main-content">
      <h1 class="description__title">Выдача градостроительного плана земельного участка</h1>
      <p class="description__text">Градостроительный план земельного участка выдается в целях обеспечения субъектов градостроительной деятельности информацией, необходимой для архитектурно-строительного проектирования, строительства, реконструкции объектов капитального строительства в границах земельного участка.</p>
    </div>
    
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
  @media(max-width: 576px) {
    max-width: $whole-content-width-mobile;
  }
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  opacity: .9;
}
.description__main-content {
  max-width: $main-content-width;
}
.description__title {
  @include responsive-font(48, 15);
}
.description__text {
  padding: 1.3rem 0 2.4rem 0;
}
.side-content {
  display: flex;
  flex-direction: column;
  @include responsive-font(14, 8);
}
.eagle-logo {
  margin-top: 1rem;
  max-width: 3.4rem;
}
.side-content__bold-text {
  font-weight: bold;
  padding: 1rem 0 .5rem 0;
}
</style>