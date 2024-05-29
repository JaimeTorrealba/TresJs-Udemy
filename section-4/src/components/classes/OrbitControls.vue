<script setup lang="ts">
import { extend, useTresContext } from '@tresjs/core'
import { OrbitControls } from 'three/addons/controls/OrbitControls'


const { camera,  renderer} = useTresContext()
// Añadimos OrbitControls al catalogo interno
extend({ OrbitControls })
</script>

<template>
    <TresOrbitControls
      v-if="renderer"
      :args="[camera, renderer?.domElement]"
    />
</template>