<template>
  <div id="app">
    <header>
      <Logos/>
    </header>

    <div class="main-content">
      <Steps/>
    </div>

    <footer>
      <InfoLinks/>
    </footer>
  </div>
</template>

<script>
import Logos from "./components/Workshop/Logos";
import Steps from "./components/Workshop/Steps";
import InfoLinks from "./components/Workshop/InfoLinks";

export default {
  name: "App",
  components: {
    Logos,
    Steps,
    InfoLinks
  }
};
</script>


<style>
#app {
  height: 100%;
  width: 100%;
  display: table;
}

.main-content {
  height: calc(100% - 250px);
  padding: 25px;
}
</style>
