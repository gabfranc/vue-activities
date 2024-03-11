<script setup>
import { ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const showText = ref(false);
const message = ref('SHOW STORE');
function clickButton() {
  showText.value = !showText.value;
}
</script>
<template>
  <main>
    <section>
      <h1>ALBUM STORE (TAYLOR'S VERSION)</h1>
      <HelloWorld v-if="showText" />
      <button @click="clickButton"><slot>{{ message }}</slot></button>

    </section>


  </main>
  
</template>


<style>
main {
  padding: 2rem;
}
.sale-tag {
  background-color: blue;
  padding: 12px;
  color: white;
}
.warn {
  background-color: rgb(226, 121, 121);
  color: rgb(137, 5, 5);
  padding: 8px;
}
</style>
