<template>
  <model-viewer
    ref="modelViewerRef"
    @mousedown="$emit('mousedown-model', $event, openMarker)"
  >
    <slot :openMarker="openMarker" :openedMarker="openedMarker"></slot>
  </model-viewer>
</template>
<script setup lang="ts">
import "@google/model-viewer";
import { ModelViewerElement } from "@google/model-viewer";
const modelViewerRef = ref<ModelViewerElement>();

const openedMarker = ref(null);

const openMarker = (marker) => {
  if (!marker) {
    openedMarker.value = null;
    return;
  }
  if (!modelViewerRef.value) return;
  if (openedMarker.value === marker.id) {
    openedMarker.value = null;
    return;
  }
  openedMarker.value = marker.id;
  const dataset = marker.dataset;
  modelViewerRef.value.cameraTarget = dataset.position;
};
</script>
