<script setup>
import { TresCanvas } from '@tresjs/core'
import { OrbitControls, Stars } from '@tresjs/cientos'
import TheEarth from './earth/TheEarth.vue'

</script>

<template>
  <TresCanvas window-size shadows clear-color="#111">
    <TresPerspectiveCamera :position="[0, 3, 5]" :look-at="[0, 0, 0]" />
    <OrbitControls />
    <Stars />
    <Suspense>
      <TheEarth />
    </Suspense>
    <TresDirectionalLight  cast-shadow :color="0xffffff" :intensity="0.5" :position="[1, 10, 1]"
    :shadow-camera-far="50" />
    <TresAmbientLight :color="0xffffff" :intensity="0.5" />
  </TresCanvas>
</template>