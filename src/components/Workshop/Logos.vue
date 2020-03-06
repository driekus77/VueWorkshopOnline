<template>
  <div class="logos">
    <div class="row inner-logo">
      <div class="logo col-5">
        <img
          src="https://www.bloemert.com/wp-content/uploads/2019/02/Logo-Bloemert-diap.png"
          style="height:75px"
        >
      </div>
      <div class="logo col-2">
        <i
          class="icon fas fa-hands-helping fa-3x"
          style="margin-top: 5px;transform: rotate(30deg);"
        ></i>
      </div>
      <div class="logo col-5">
        <img src="https://vuejs.org/images/logo.png" style="height:75px;">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Logos"
};
</script>

<style>
.row {
  display: flex;
  height: 100px;
}

.icon {
  color: var(--bloemertlight-color);
  vertical-align: middle;
  text-align: center;
}

.logo {
  flex: 0 0 auto;
  padding: 10px;
  vertical-align: middle;
  margin: auto;
}

.logos {
  vertical-align: middle;
  margin: auto;
  padding: 10px;
  background-color: var(--bloemertdark-color);
  border-radius: 15px;
  box-shadow: 5px 5px 5px var(--bloemertshadow-color);
}
</style>