<template>
  <router-link to="/">home</router-link> |
  <router-link to="/about">about</router-link>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
});
</script>

<style>
</style>
