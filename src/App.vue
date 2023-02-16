<template>
  <v-text-field
    variant="outlined"
    label="Name"
    clearable
    v-model="name"
  ></v-text-field>
  <v-btn @click="greet">Click me to greet.</v-btn>
  <v-label>{{ greetMsg }}</v-label>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";

const greetMsg = ref("");
const name = ref("");

async function greet() {
  greetMsg.value = await invoke("greet", { name: name.value });
}
</script>

<style scoped></style>
