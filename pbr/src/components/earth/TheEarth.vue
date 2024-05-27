<script setup>
import { shallowRef } from 'vue';
import { useLoop, useTexture } from '@tresjs/core'

const sphereRef = shallowRef(null)

const { map } = await useTexture({
    map: '/textures/8k_earth_daymap.jpg',
})

console.log('jaime ~ map:', map);
const { onBeforeRender } = useLoop()

onBeforeRender(({elapsed}) => {
    sphereRef.value.rotation.y = elapsed *0.5
})

</script>

<template>
    <TresMesh ref="sphereRef" >
        <TresSphereGeometry :args="[1, 16]" />
        <TresMeshStandardMaterial :map="map" />
    </TresMesh>
</template>