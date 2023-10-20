<script setup lang="ts">
const props = defineProps<{
  configUrl: string;
}>();

useHead({
  script: [{ src: "js/object2vr_player.js" }, { src: "HTML/skin.js" }],
});

onMounted(() => {
  const obj = new object2vrPlayer("container") as unknown as Object2VR;

  // Monkey-patch toggleFullscreen to disable fulscreen
  obj.toggleFullscreen = function () {};

  obj.readConfigUrl(props.configUrl);
});
</script>

<template>
  <div id="container"></div>
</template>
