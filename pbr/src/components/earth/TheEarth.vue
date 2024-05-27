<script setup>
import { shallowRef } from 'vue';
import { useLoop, useTexture, vLog } from '@tresjs/core'
import { Vector3, MathUtils } from 'three'

const sphereRef = shallowRef(null)
const cloudsRef = shallowRef(null)

const { map, normalMap, alphaMap } = await useTexture({
    map: '/textures/8k_earth_daymap.jpg',
    normalMap: '/textures/8k_earth_normal_map.jpg',
    alphaMap: '/textures/8k_earth_clouds.jpg'
})

const latLng = () => {
    return new Vector3().setFromSphericalCoords(
        1,
        MathUtils.degToRad(90 - 53.845), // lat
        MathUtils.degToRad(90 + -1.949), // lng
    )
}
console.log('jaime ~ latLng ~ latLng:', latLng());

const { onBeforeRender } = useLoop()

onBeforeRender(({ elapsed }) => {
    sphereRef.value.rotation.y = elapsed * 0.15
    cloudsRef.value.rotation.y = elapsed * 0.25
})

</script>

<template>
    <TresGroup ref="sphereRef">
        <TresMesh >
            <TresSphereGeometry :args="[1, 32]" />
            <TresMeshStandardMaterial :map="map" :normalMap="normalMap" :normal-scale="[5, 5]" />
        </TresMesh>
        <TresMesh :position="[...latLng()]">
            <TresSphereGeometry :args="[0.01, 32]" />
            <TresMeshBasicMaterial />
        </TresMesh>
    </TresGroup>
    <TresMesh ref="cloudsRef">
        <TresSphereGeometry :args="[1.01, 32]" />
        <TresMeshStandardMaterial v-log transparent :alphaMap="alphaMap" />
    </TresMesh>
</template>