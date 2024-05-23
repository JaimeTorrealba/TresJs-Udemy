<script setup>
import { shallowRef } from 'vue';
import { useLoop } from '@tresjs/core'

const sphereRef = shallowRef(null)

const { onBeforeRender } = useLoop()

onBeforeRender(({elapsed}) => {
    sphereRef.value.position.z = Math.sin(elapsed)
})

</script>

<template>
    <TresMesh ref="sphereRef" cast-shadow >
        <TresSphereGeometry :args="[1, 16]" />
        <TresMeshStandardMaterial />
    </TresMesh>
    <TresMesh receive-shadow :rotation-x="-Math.PI * 0.5" :position-y="-2" >
        <TresPlaneGeometry :args="[10, 10]" />
        <TresMeshStandardMaterial color="#f7f7f7" />
    </TresMesh>
    
</template>