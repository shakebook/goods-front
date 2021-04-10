<template>
  <div class="about">
    <h1>{{ home.account.accountName }}-{{ about.count }}</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useStore } from "@/store";

export default defineComponent({
  name: "Abount",
  setup() {
    const { home, about } = useStore().state;
    return { about, home };
  },
});
</script>