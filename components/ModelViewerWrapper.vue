<template>
  <model-viewer ref="modelViewerRef" @mousedown="onMousedown">
    <template v-for="(marker, i) in markersData">
      <button
        :ref="setComponentRef(i)"
        @click="(e) => openMarker(e.target as HTMLElement)"
        :slot="`hotspot-${i + 1}`"
        :data-position="marker.dataPosition"
        :data-normal="marker.dataNormal"
        data-visibility-attribute="visible"
        :id="`hotspot-${i + 1}`"
      >
        <PulsatingMarker
          class="pointer-events-none visible flex h-16 w-16 items-center justify-center"
          :open="openedMarker === `hotspot-${i + 1}`"
        >
          {{ i + 1 }}
        </PulsatingMarker>
      </button>
      <TransitionOpacity>
        <Annotation
          @onPrevClick="
            openMarker(
              i > 0 ? markersRefs[i - 1] : markersRefs[markersRefs.length - 1],
            )
          "
          @onNextClick="
            openMarker(
              i < markersRefs.length - 1 ? markersRefs[i + 1] : markersRefs[0],
            )
          "
          class="absolute bottom-0 right-0 z-10"
          v-if="openedMarker === `hotspot-${i + 1}`"
        >
          <template #header>{{ `${i + 1}. ${marker.title}` }}</template>
          <template #body
            ><span>{{ marker.body }}</span></template
          >
        </Annotation>
      </TransitionOpacity>
    </template>
    <slot :openMarker="openMarker" :openedMarker="openedMarker"></slot>
  </model-viewer>
</template>
<script setup lang="ts">
import "@google/model-viewer";
import { ModelViewerElement } from "@google/model-viewer";

defineProps(["markersData"]);

const modelViewerRef = ref<ModelViewerElement>();
const openedMarker = ref<string | null>(null);
const markersRefs = ref<Array<HTMLElement>>([]);
const setComponentRef = (index: number) => (ref: HTMLElement) => {
  markersRefs.value[index] = ref;
  return undefined;
};

const onMousedown = (e: any) => {
  const panning = e.button === 2 || e.ctrlKey || e.metaKey || e.shiftKey;
  if (!panning) return;
  openMarker(null);
};

const openMarker = (marker: HTMLElement | null) => {
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
  if (!dataset.position) {
    return;
  }
  modelViewerRef.value.cameraTarget = dataset.position;
};
</script>
