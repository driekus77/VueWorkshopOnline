<template>
  <div>
    <vue-markdown :source="info"/>
  </div>
</template>

<script>
//import Vue from 'vue';
import axios from "axios";
import VueMarkdown from "vue-markdown";
//Vue.use(VueMarkdown);

export default {
  name: "Step",
  data() {
    return {
      info: null
    };
  },
  props: ["value"],
  mounted() {
    axios
      .get("/Steps/" + this.value)
      .then(response => (this.info = response.data));
  },
  watch: {
    value() {
      axios
        .get("/Steps/" + this.value)
        .then(response => (this.info = response.data));
    }
  },
  components: {
    VueMarkdown
  }
};
</script>
