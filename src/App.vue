<template>
  <div id="app">
    <header>
      <Logos/>
    </header>

    <Steps style="height: calc(100% - 325px);margin-top:50px"/>

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
</style>
