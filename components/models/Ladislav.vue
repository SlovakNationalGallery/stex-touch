<template>
  <ClientOnly>
    <ModelViewerWrapper
      class="h-full w-full"
      alt="Neil Armstrong's Spacesuit from the Smithsonian Digitization Programs Office and National Air and Space Museum"
      src="assets/models/ladislav/ladislav.gltf"
      shadow-intensity="1"
      camera-controls
      @mousedown-model="onMousedown"
      touch-action="pan-y"
      v-slot="{ openMarker, openedMarker }"
    >
      <template v-for="(marker, i) in markersData">
        <button
          :ref="setComponentRef(i)"
          @click="(e) => openMarker(e.target)"
          :slot="marker.id"
          :data-position="marker.dataPosition"
          :data-normal="marker.dataNormal"
          data-visibility-attribute="visible"
          :id="marker.id"
        >
          <PulsatingMarker
            class="pointer-events-none visible flex h-16 w-16 items-center justify-center"
            :open="openedMarker === marker.id"
          >
            {{ i + 1 }}
          </PulsatingMarker>
        </button>
        <TransitionOpacity>
          <Annotation
            @onPrev="
              openMarker(
                i > 0
                  ? markersRefs[i - 1]
                  : markersRefs[markersRefs.length - 1],
              )
            "
            @onNext="
              openMarker(
                i < markersRefs.length - 1
                  ? markersRefs[i + 1]
                  : markersRefs[0],
              )
            "
            class="absolute bottom-0 right-0 z-10"
            v-if="openedMarker === marker.id"
          >
            <template #header>{{ `${i + 1}. ${marker.title}` }}</template>
            <template #body
              ><span>{{ marker.body }}</span></template
            >
          </Annotation>
        </TransitionOpacity>
      </template>
    </ModelViewerWrapper>
  </ClientOnly>
</template>
<script setup>
const markersRefs = ref([]);

const setComponentRef = (index) => (ref) => {
  markersRefs.value[index] = ref;
};

const onMousedown = (e, openMarker) => {
  const panning = e.button === 2 || e.ctrlKey || e.metaKey || e.shiftKey;
  if (!panning) return;
  openMarker(null);
};

const markersData = [
  {
    title: "Nos",
    body: "Cupcake ipsum dolor sit amet pie. Liquorice carrot cake I love I love gummies dessert. Chocolate bar wafer brownie jelly-o halvah apple pie sweet sesame snaps gingerbread. Tart tart cake chupa chups chocolate bar wafer apple pie ice cream. Dragée I love I love ice cream I love jelly. Candy liquorice gingerbread macaroon apple pie jelly.",
    id: "hotspot-1",
    dataPosition:
      "-0.03202602775138658m 0.4090752933558993m 0.05194060924962036m",
    dataNormal: "-0.724787383971703m -0.5828204897817553m 0.36742825793072903m",
  },
  {
    title: "Ruka",
    body: "Cupcake ipsum dolor sit amet pie. Liquorice carrot cake I love I love gummies dessert. Chocolate bar wafer brownie jelly-o halvah apple pie sweet sesame snaps gingerbread. Tart tart cake chupa chups chocolate bar wafer apple pie ice cream. Dragée I love I love ice cream I love jelly. Candy liquorice gingerbread macaroon apple pie jelly.",
    id: "hotspot-2",
    dataPosition:
      "0.04716799564096756m 0.1988430793234805m 0.0900607777099296m",
    dataNormal: "0.21696173399728239m -0.03611846436971602m 0.975511692657995m",
  },
];
</script>
