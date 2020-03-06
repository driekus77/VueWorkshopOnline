<template>
  <vue-markdown
    name="MarkdownInfoArea"
    id="MarkdownInfoArea"
    lang-prefix="line-numbers language-"
    :source="info"
  />
</template>

<script>
import axios from "axios";
import Vue from "vue";
import VueMarkdown from "vue-markdown";

import Prism from "prismjs";
import PrismLN from "prismjs/plugins/line-numbers/prism-line-numbers";
import "prismjs/themes/prism.css";
import "prismjs/plugins/line-numbers/prism-line-numbers.css";

import _ from "lodash";

Vue.use(VueMarkdown);

export default {
  name: "Step",
  data() {
    return {
      info: "Loading."
    };
  },
  props: ["value"],
  mounted() {
    axios
      .get("/Steps/" + this.value)
      .then(
        response =>
          (this.info = _.isEmpty(response.data) ? "Loading..." : response.data)
      );
  },
  watch: {
    value() {
      axios
        .get("/Steps/" + this.value)
        .then(
          response =>
            (this.info = _.isEmpty(response.data)
              ? "Loading..."
              : response.data)
        );
    }
  },
  components: {
    VueMarkdown
  },
  updated: function() {
    Prism.highlightAll();
  }
};
</script>
