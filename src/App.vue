<template>
  <div id="app">
    <Header />
    <Description />
    <Forms />
  </div>
</template>

<script>
import Header from './components/Header'
import Description from './components/Description'
import Forms from './components/Forms'

export default {
  name: 'App',
  components: {
    Header,
    Description,
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
    font-family: sans-serif;
    background: $light-grey;
}
</style>
