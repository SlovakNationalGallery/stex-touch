<template>
  <ClientOnly>
    <ModelViewerWrapper
      class="h-full w-full"
      alt="Neil Armstrong's Spacesuit from the Smithsonian Digitization Programs Office and National Air and Space Museum"
      src="assets/models/ladislav/ladislav.gltf"
      shadow-intensity="1"
      camera-controls
      touch-action="pan-y"
    >
      <button
        class="w-6 h-6 pointer-events-none block bg-red-300 rounded-full"
        slot="hotspot-1"
        data-position="-0.03202602775138658m 0.4090752933558993m 0.05194060924962036m"
        data-normal="-0.724787383971703m -0.5828204897817553m 0.36742825793072903m"
        data-visibility-attribute="visible"
      >
      </button>
      <button
        class="w-6 h-6 pointer-events-none block bg-red-300 rounded-full"
        slot="hotspot-2"
        data-position="0.04716799564096756m 0.1988430793234805m 0.0900607777099296m"
        data-normal="0.21696173399728239m -0.03611846436971602m 0.975511692657995m"
        data-visibility-attribute="visible"
      >
      </button>
      <button
        class="w-6 h-6 pointer-events-none block bg-red-300 rounded-full"
        slot="hotspot-3"
        data-position="-0.06460396014077777m -0.24856338199124775m 0.08168730496036329m"
        data-normal="-0.07632463034388531m 0.5920921430510778m 0.8022477453630215m"
        data-visibility-attribute="visible"
      >
      </button>
    </ModelViewerWrapper>
  </ClientOnly>
</template>
