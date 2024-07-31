<script setup>
import { shallowRef } from 'vue'
import { useLoop, useTexture } from '@tresjs/core'
import { CatmullRomCurve3, Vector3, BackSide, RepeatWrapping } from 'three'

const { map, aoMap, normalMap } = await useTexture({
    map: '/textures/Alien_Flesh_001_color.jpg',
    aoMap: '/textures/Alien_Flesh_001_norm.jpg',
    normalMap: '/textures/Alien_Flesh_001_spec.jpg'
})
console.log('jaime ~ map:', map);

const tubeMaterialRef = shallowRef()

const points = []

for (let i = 0; i < 5; i++) {
    points.push(new Vector3(0, 0, 2.5 * (i / 4)))
}

const curve = new CatmullRomCurve3(points)

const { onBeforeRender } = useLoop()

onBeforeRender(() => {
    if (tubeMaterialRef.value) {
        tubeMaterialRef.value.map.offset.x += 0.001
        tubeMaterialRef.value.aoMap.offset.x += 0.001
        tubeMaterialRef.value.normalMap.offset.x += 0.001
    }
})
</script>
<template>
    <TresMesh :position-z="-2">
        <TresTubeGeometry :args="[curve, 70, 0.02, 50, false]" />
        <TresMeshStandardMaterial ref="tubeMaterialRef" :map="map" :map-wrapS="RepeatWrapping"
            :map-wrapT="RepeatWrapping" :normalMap="normalMap" :normalMap-wrapS="RepeatWrapping"
            :normalMap-wrapT="RepeatWrapping" :aoMap="aoMap" :side="BackSide" :aoMap-wrapS="RepeatWrapping"
            :aoMap-wrapT="RepeatWrapping" />
    </TresMesh>
</template>