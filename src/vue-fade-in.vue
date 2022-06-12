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
    initNodes(wrapper) {
      try {
        wrapper.childNodes.forEach((node) => this.initNode(node));

        this.startFade(wrapper);
      } catch {
        setTimeout(() => {
          this.initNodes(wrapper);
        }, 100);
      }
    },

    initNode(node) {
      node.style.transition = `opacity ${this.trasitionDuration}ms, transform ${this.trasitionDuration}ms`;
    },
    showNode(node) {
      node.style.transform = "translateY(0px)";
      node.style.opacity = 1;
    },

    async startFade(wrapper) {
      for (let i = 0; i < wrapper.childNodes.length; i++) {
        await this.timeout(this.delay);
        this.showNode(wrapper.childNodes[i]);
      }
    },

    timeout(delay) {
      return new Promise((resolve) => setTimeout(resolve, delay));
    },
  },
  mounted() {
    this.$nextTick(() => {
      this.initNodes(this.$refs.vueFadeIn);
    });
  },
};
</script>

<template>
  <div ref="vueFadeIn" id="vue-fade-in"><slot /></div>
</template>

<style>
#vue-fade-in > * {
  opacity: 0;
  transform: translateY(20px);
}
</style>
