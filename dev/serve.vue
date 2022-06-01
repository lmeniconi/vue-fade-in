<script>
import Vue from "vue";
import VueFadeIn from "@/vue-fade-in.vue";
import Test from "./Test.vue";

export default Vue.extend({
  components: {
    VueFadeIn,
    Test,
  },
  data() {
    return {
      show: false,
    };
  },
  created() {
    setTimeout(() => (this.show = true), 1000);
  },
});
</script>

<template>
  <div id="app">
    <VueFadeIn v-if="show">
      <Test v-for="i in 10" :key="i" />

      <div><div>jojo</div></div>
    </VueFadeIn>
  </div>
</template>
