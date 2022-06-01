<script>
export default {
  name: "VueFadeIn",
  data() {
    return {
      show: false,
    };
  },
  props: {
    delay: {
      type: Number,
      default: 50,
    },
    trasitionDuration: {
      type: Number,
      default: 300,
    },
  },
  methods: {
    async startFade(wrapper) {
      for (let i = 0; i < wrapper.childNodes.length; i++) {
        await this.timeout(this.delay);
        this.showNode(wrapper.childNodes[i]);
      }
    },

    initNodes(wrapper) {
      wrapper.childNodes.forEach((node) => this.initNode(node));
      this.show = true;
    },
    initNode(node) {
      node.style.transition = `opacity ${this.trasitionDuration}ms, transform ${this.trasitionDuration}ms`;
      node.style.transform = "translateY(20px)";
      node.style.opacity = 0;
    },

    showNode(node) {
      node.style.transform = "translateY(0px)";
      node.style.opacity = 1;
    },

    timeout(delay) {
      return new Promise((resolve) => setTimeout(resolve, delay));
    },
  },
  mounted() {
    this.initNodes(this.$refs.vueFadeIn);
    this.startFade(this.$refs.vueFadeIn);
  },
};
</script>

<template>
  <div v-show="show" ref="vueFadeIn" id="vue-fade-in"><slot /></div>
</template>
