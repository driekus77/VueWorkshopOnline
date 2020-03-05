<template>
  <div id="app">
    <header class="header">
      <Logo/>
      <h1>
        Welcome to the
        <span class="bloemert">Bloemert</span> -
        <span class="vue">Vue.js</span> workshop!
      </h1>
    </header>

    <h2 style="margin:10px;">Step 1: Basics</h2>
    <div class="content">
      <p>Hier komt de StepX.md inhoud?</p>
    </div>

    <footer class="footer">
      <InfoLinks/>
    </footer>
  </div>
</template>

<script>
import Logo from "./components/Logo";
import InfoLinks from "./components/InfoLinks";

export default {
  name: "App",
  components: {
    Logo,
    InfoLinks
  }
};
</script>

<style>
:root {
  --bloemertlight-color: rgba(174, 142, 67, 1);
  --bloemertdark-color: rgba(2, 21, 49, 1);
  --bloemertshadow-color: rgba(2, 21, 49, 0.5);
  --vue-color: rgba(66, 185, 131, 1);
  --vuedark-color: rgba(52, 73, 94, 1);
}

* {
  padding: 0;
  margin: 0;
}

html,
body {
  min-height: calc(100vh) !important;
  max-height: 100%;
  height: 100%;

  overflow: hidden;
}

#app {
  font-family: "Roboto", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;

  display: flex;
  flex-direction: column;
  height: calc(97vh);
}

.bloemert {
  color: var(--bloemertlight-color);
}

.vue {
  color: var(--vue-color);
}

.content {
  flex: 1 0 auto;
  /* Prevent Chrome, Opera, and Safari from letting these items shrink to smaller than their content's default minimum size. */
  padding: 10px;
}

.footer {
  flex-shrink: 0;
  /* Prevent Chrome, Opera, and Safari from letting these items shrink to smaller than their content's default minimum size. */
  padding: 10px;
  background-color: var(--vuedark-color);
  color: var(--bloemertlight-color);
}
</style>
