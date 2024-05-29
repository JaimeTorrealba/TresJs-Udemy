<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import ThePrimitive from './classes/ThePrimitive.vue'
</script>

<template>
    <TresCanvas clear-color="#333" window-size>
        <TresPerspectiveCamera :position="[3, 3, 3]" :look-at="[0, 0, 0]" />
        <ThePrimitive />
        <OrbitControls />
    </TresCanvas>
</template>