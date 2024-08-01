<script setup>
import { Sky, Box, HolographicMaterial } from '@tresjs/cientos'
</script>
<template>
    <Box :args="[2, 1, 3]">
        <HolographicMaterial />
    </Box>
    <!-- <TresMesh>
        <TresBoxGeometry :width='1' :height='1' :depth='1' />
    </TresMesh> -->
    <Sky />
</template>