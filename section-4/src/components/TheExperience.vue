<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { OrbitControls} from '@tresjs/cientos'
// import OrbitControls from './classes/OrbitControls.vue'
</script>

<template>
    <TresCanvas clear-color="#333" window-size>
        <TresPerspectiveCamera :position="[3, 3, 3]" :look-at="[0, 0, 0]" />
        <TresMesh>
            <TresTorusGeometry :args="[1, 0.5, 16, 32]" />
            <TresMeshBasicMaterial color="orange" />
        </TresMesh>
        <OrbitControls />
    </TresCanvas>
</template>