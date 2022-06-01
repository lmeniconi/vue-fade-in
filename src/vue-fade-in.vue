<script>
export default {
  name: "VueFadeIn",
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
  <div ref="vueFadeIn" id="vue-fade-in"><slot /></div>
</template>
