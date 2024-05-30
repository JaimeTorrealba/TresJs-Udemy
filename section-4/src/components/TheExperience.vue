<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import SelectableGrid from './classes/SelectableGrid.vue'
</script>

<template>
    <TresCanvas clear-color="#333" window-size>
        <TresPerspectiveCamera :position="[0, 10, 10]" :look-at="[0, 0, 0]" />
        <SelectableGrid />
        <OrbitControls />
    </TresCanvas>
</template>