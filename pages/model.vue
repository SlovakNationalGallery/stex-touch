<template>
  <div class="absolute inset-0 flex flex-col items-center">
    <h1 class="mt-8 text-center text-xl">3D Model</h1>
    <div class="mt-4 h-2/3 w-1/2 rounded-md border p-4">
      <ClientOnly>
        <ModelViewerWrapper
          :markersData="[
            {
              title: 'Nos',
              body: 'Cupcake ipsum dolor sit amet pie. Liquorice carrot cake I love I love gummies dessert. Chocolate bar wafer brownie jelly-o halvah apple pie sweet sesame snaps gingerbread. Tart tart cake chupa chups chocolate bar wafer apple pie ice cream. Dragée I love I love ice cream I love jelly. Candy liquorice gingerbread macaroon apple pie jelly.',
              dataPosition:
                '-0.03202602775138658m 0.4090752933558993m 0.05194060924962036m',
              dataNormal:
                '-0.724787383971703m -0.5828204897817553m 0.36742825793072903m',
            },
            {
              title: 'Ruka',
              body: 'Cupcake ipsum dolor sit amet pie. Liquorice carrot cake I love I love gummies dessert. Chocolate bar wafer brownie jelly-o halvah apple pie sweet sesame snaps gingerbread. Tart tart cake chupa chups chocolate bar wafer apple pie ice cream. Dragée I love I love ice cream I love jelly. Candy liquorice gingerbread macaroon apple pie jelly.',
              dataPosition:
                '0.04716799564096756m 0.1988430793234805m 0.0900607777099296m',
              dataNormal:
                '0.21696173399728239m -0.03611846436971602m 0.975511692657995m',
            },
          ]"
          class="h-full w-full"
          alt="Neil Armstrong's Spacesuit from the Smithsonian Digitization Programs Office and National Air and Space Museum"
          src="assets/models/ladislav/ladislav.gltf"
          shadow-intensity="1"
          camera-controls
          touch-action="pan-y"
          interaction-prompt-style="basic"
        ></ModelViewerWrapper>
      </ClientOnly>
    </div>
  </div>
</template>
