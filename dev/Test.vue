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
    const array = [100, 500, 1000];

    const randomElement = array[Math.floor(Math.random() * array.length)];
    setTimeout(() => {
      this.content = "<h1>Hola wenas</h1>" + `${randomElement}`;
    }, randomElement);
  },
};
</script>
