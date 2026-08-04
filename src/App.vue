<template>
  <div>
    <PassGen />
  </div>
</template>

<script>
import PassGen from "./components/PassGen.vue";

export default {
  name: "App",
  components: {
    PassGen,
  },
};
</script>

<style>
* {
  font-family: "Montserrat", sans-serif;
}
body {
  background-image: url(../src/imgs/bg.svg);
  background-repeat: no-repeat;
  background-attachment: fixed;
}
</style>
