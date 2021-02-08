<template>
  <div id="app">
    <Header />
    <Description />
    <HorizontalLine />
    <Forms />
  </div>
</template>

<script>
import Header from './components/Header'
import Description from './components/Description'
import Forms from './components/Forms'
import HorizontalLine from './components/HorizontalLine'

export default {
  name: 'App',
  components: {
    Header,
    Description,
    HorizontalLine,
    Forms
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
:root {
    @include responsive-font(18, 10);
    font-family: 'GOST UI 2', sans-serif;
    background: $lighter-grey;
    color: $dark-grey;
}
</style>
