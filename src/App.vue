<script >
import TheMain from "./components/TheMain.vue"
import TheHeader from "./components/TheHeader.vue"
import Select from "./components/Select.vue"



export default {
  components: {
    TheMain,
    TheHeader,
    Select,

  }
}
</script>

<template>
  <header>
    <TheHeader></TheHeader>
  </header>
  <div class="container select">
    <Select></Select>
  </div>
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
    margin-top: 20px;
    background-color: white;
    width: 1000px;
    padding: 50px;
  }


}

.select {
  margin-left: 200px;
}
</style>
