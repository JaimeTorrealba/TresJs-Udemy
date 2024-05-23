<script setup>
import { shallowRef, watch } from 'vue'
import { TresCanvas, vLightHelper } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import TheEarth from './earth/TheEarth.vue'
import { CameraHelper } from 'three'

const lightRef = shallowRef(null)

watch(lightRef, light => {
  // light.shadow.mapSize.width = 1024
  // light.shadow.mapSize.height = 1024
  // light.shadow.camera.near = 0.5
  // light.shadow.camera.far = 50
  console.log('jaime ~ light:', light);
  const helper = new CameraHelper(light.shadow.camera);
  light.parent.add(helper);
})
</script>

<template>
  <TresCanvas window-size shadows clear-color="#111">
    <TresPerspectiveCamera :position="[0, 3, 5]" :look-at="[0, 0, 0]" />
    <OrbitControls />
    <TheEarth />
    <TresDirectionalLight ref="lightRef" cast-shadow :color="0xffffff" :intensity="0.5" :position="[1, 10, 1]"
    :shadow-camera-far="50"
      v-light-helper />
  </TresCanvas>
</template>