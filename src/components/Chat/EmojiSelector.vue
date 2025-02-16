<script setup>
import Button from "../generic/form/Button.vue";
import useIcons from "../../compositionFunctions/useIcons";

// Components emit events. Parent components listen to these events. Just like the DOM!
const emit = defineEmits(["sendEmoji"]);
const allIcons = useIcons();
const icons = Object.keys(allIcons).filter((icon) => icon !== "send");

function send(iconName) {
  emit("sendEmoji", iconName);
}
</script>

<template>
  <div class="emoji-selector">
    <Button
      v-for="icon in icons"
      :key="icon"
      :icon="icon"
      :alt="`${icon}-emoji`"
      @click="send(icon)"
    />
  </div>
</template>

<style scoped>
.emoji-selector {
  display: inline-flex;
  gap: 0.25rem;
  border-radius: 2rem;
  padding: 0.25rem;
  background-color: white;
}
</style>
