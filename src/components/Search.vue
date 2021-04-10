<template>
  <div class="flex f-row middle center container">
    <img class="logo" src="@/assets/logo.png" alt="" />
    <div class="flex f-row search">
      <input v-model.trim="keywords" type="text" />
      <div class="flex f-row middle search-right">
        <img
          v-if="showClear"
          @click="onClear"
          class="clear"
          src="@/assets/clear.svg"
          alt="clear"
        />
        <div @click="submit" class="search-button flex middle center">
          <img class="submit" src="@/assets/search.svg" alt="submit" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watchEffect } from "vue";
export default defineComponent({
  name: "Search",
  setup() {
    const keywords = ref("");
    const showClear = ref(false);

    const onChange = () => {
      showClear.value = keywords.value !== "" ? true : false;
    };

    const onClear = () => {
      keywords.value = "";
      showClear.value = false;
    };

    //监听
    watchEffect(() => {
      onChange();
    });

    const submit = () => {
      console.log("keywords", keywords.value);
    };

    return { keywords, showClear, onClear, submit };
  },
});
</script>

<style scoped>
.container {
  width: 38%;
  max-width: 500px;
}

.logo {
  width: 100px;
}

.search-right {
  position: absolute;
  top: 1px;
  right: 1px;
  bottom: 1px;
  border-top-right-radius: 39px;
  border-bottom-right-radius: 39px;
  background-color: #fff;
}

.search-button {
  background: rgb(247, 247, 247);
  border-top-right-radius: 39px;
  border-bottom-right-radius: 39px;
  height: 100%;
  width: 70px;
  cursor: pointer;
  border-left: 1px solid rgb(237, 237, 237);
}

.submit {
  height: 30px;
}

.clear {
  height: 30px;
  cursor: pointer;
}

.split {
  height: 25px;
}

.search {
  flex: 1;
  position: relative;
}

.container input {
  height: 39px;
  margin-left: 10px;
  border-radius: 39px;
  outline: none;
  border: 1px solid #ddd;
  text-indent: 10px;
  color: #555;
  font-size: 17px;
  flex: 1;
}

.container input:hover {
  box-shadow: #ddd 0px 0px 5px;
}
</style>
