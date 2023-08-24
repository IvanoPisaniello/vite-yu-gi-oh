<script >
import TheMain from "./components/TheMain.vue"
import TheHeader from "./components/TheHeader.vue"


export default {
  components: {
    TheMain,
    TheHeader,
  }
}
</script>

<template>
  <header>
    <TheHeader></TheHeader>
  </header>
  <main class="main-section">
    <div class="cards-container container">
      <TheMain></TheMain>
    </div>
  </main>
</template>

<style lang="scss">
body {
  background-color: orange;
}

.main-section {
  background-color: orange;


  .cards-container {
    margin-top: 100px;
    background-color: white;
    width: 1000px;
    padding: 50px;
  }

}
</style>
