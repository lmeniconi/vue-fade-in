<template>
  <div v-if="content" v-html="content"></div>
</template>

<script>
export default {
  data() {
    return {
      content: "",
    };
  },
  created() {
    setTimeout(() => {
      this.content = "<h1>Hola wenas</h1>";
    }, 50);
  },
};
</script>
