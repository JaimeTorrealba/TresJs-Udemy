<script setup>
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import TheCientos from './classes/TheCientos.vue'

</script>
<template>
    <TresCanvas window-size clear-color='#111'>
        <TresPerspectiveCamera :position='[0, 0, -15]' :fov='45' :aspect='1' :near='0.1' :far='1000' />
        <OrbitControls />
        <Suspense>
            <TheCientos />
        </Suspense>
        <TresDirectionalLight :position='[0, 0, -10]' :intensity="30" />
    </TresCanvas>
</template>