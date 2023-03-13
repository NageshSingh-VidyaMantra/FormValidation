<script setup>
import { ref } from "vue";
const props = defineProps(["usernameEmpty", "usernameFocused"]);
const emits = defineEmits(["userNameHandler"]);
const username = ref();

function onChangeHandler() {
  // username._value.value --> DOM value of Input Field
  emits("userNameHandler", username._value.value);
}
</script>

<template>
  <div class="flex justify-between items-center my-5">
    <label class="text-purple-400 font-bold text-xl">Name</label>
    <div>
      <input
        @change="onChangeHandler"
        ref="username"
        type="text"
        class="w-[250px] rounded-md py-1 pl-2 focus:border-2 focus:outline-purple-400"
        :class="[usernameEmpty && usernameFocused ? 'emptyFalse' : 'emptyTrue']"
        placeholder="Username"
      />
      <p
        class="text-red-400 text-sm"
        :class="[usernameEmpty && usernameFocused ? 'visibleP' : 'invisibleP']"
      >
        *Username can't be Empty
      </p>
    </div>
  </div>
</template>

<style scoped>
.emptyTrue {
  @apply border-[1px] border-purple-200;
}

.emptyFalse {
  @apply border-2 bg-rose-100 border-rose-300;
}

.visibleP {
  @apply visible;
}

.invisibleP {
  @apply invisible;
}
</style>
