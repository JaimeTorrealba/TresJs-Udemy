<script setup>
import { TresCanvas, vLightHelper  } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'

</script>

<template>
  <TresCanvas window-size clear-color="#111">
    <TresPerspectiveCamera :position="[0, 3, 5]" :look-at="[0,0,0]"  />
    <OrbitControls />
    <TresMesh ref="sphereRef">
        <TresSphereGeometry :args="[1,16]" />
        <TresMeshStandardMaterial />
      </TresMesh>
      <!-- <TresAmbientLight :color="0xffffff" :intensity="0.5" /> -->
      <TresDirectionalLight :color="0xffffff" :intensity="0.5" :position="[1,10,1]" v-light-helper  />
  </TresCanvas>
</template>