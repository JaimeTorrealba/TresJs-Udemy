<script setup>
import { useTresContext } from '@tresjs/core'

const ctx = useTresContext()
console.log('jaime ~ ctx:', ctx);
</script>
<template>
    <TresMesh ref="boxRef">
        <TresBoxGeometry :args="[1,1,1]" />
        <TresMeshBasicMaterial color="green" />
      </TresMesh>
</template>