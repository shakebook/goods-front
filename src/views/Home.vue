<template></template>

<script lang="ts">
import { defineComponent, computed } from "vue";
import { useStore } from "@/store";
import * as homeTypes from "@/store/home/types";
import * as abountTypes from "@/store/about/types";

export default defineComponent({
  name: "Home",
  setup() {
    const store = useStore();
    const { home, about } = store.state;

    const changeAccount = () => {
      //store.commit(homeTypes.CHANGE_ACCOUNT, "zhangnianxia");
      store.dispatch("home/" + homeTypes.CHANGE_ACCOUNT);
    };
    const changeCounter = () => {
      store.commit("about/" + abountTypes.CHANGE_COUNTER, 9.8);
    };
    const account = computed(() => home.account);

    return { account, about, changeAccount, changeCounter };
  },
});
</script>
