<script setup>
import { ref } from "vue";
import UIModal from "./UIModal.vue";

const isModalOpened = ref(false);

const open = () => {
  isModalOpened.value = !isModalOpened.value;
}
</script>

<template>
  <main class="main">
    <button @click="open()">
      Открыть
    </button>

    <UIModal
      v-model="isModalOpened"
      @close="isModalOpened = false"
    />
  </main>
</template>

<style lang="scss">
.main {
  display: flex;
  flex: 1;

  font-family: "Montserrat", serif;
}
</style>
