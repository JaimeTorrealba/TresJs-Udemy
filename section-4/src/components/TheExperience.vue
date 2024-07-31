<script setup>
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import InfiniteTube from './classes/InfiniteTube.vue'

</script>
<template>
    <TresCanvas window-size clear-color='#111'>
        <TresFog color='#111' :near="0.6" :far="2.8" />
        <TresPerspectiveCamera :position='[0, 0, 0.35]' :fov='8' :aspect='1' :near='0.1' :far='1000' />
        <Suspense>
            <InfiniteTube />
        </Suspense>
        <TresDirectionalLight :args="[0xffffff, 0.8]" />
        <TresHemisphereLight :args="[0xffffbb, 0x887979, 0.9]" />
        <!-- <OrbitControls /> -->
    </TresCanvas>
</template>