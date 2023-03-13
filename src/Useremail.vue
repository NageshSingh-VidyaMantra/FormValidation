<script setup>
import { ref } from 'vue';
const props = defineProps(['userEmailEmpty','useremailFocused']);
const emits = defineEmits(['userEmailHandler']);
const useremail = ref();

function onChangeHandler() {
  // useremail._value.value --> DOM value of Input Field
  emits("userEmailHandler", useremail._value.value)
}
</script>

<template>
  <div class="flex justify-between items-center my-5">
    <label class="text-purple-400 font-bold text-xl">Email</label>
    <div>
      <input ref="useremail" autocomplete @change.prevent="onChangeHandler" type="email"
        class="w-[250px] rounded-md py-1 pl-2 border-[1px] border-purple-200 focus:outline-purple-400"
        :class="[userEmailEmpty && useremailFocused ? 'emptyFalse' : 'emptyTrue']" placeholder="Useremail">
        <p class="text-red-400 text-sm" :class="[userEmailEmpty && useremailFocused ? 'visibleP' : 'invisibleP']" >*Useremail can't be Empty</p>

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