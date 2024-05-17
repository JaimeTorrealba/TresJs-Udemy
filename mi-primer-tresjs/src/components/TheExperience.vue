<script lang="ts" setup>
import { TresCanvas  } from '@tresjs/core'
</script>

<template>
  <TresCanvas window-size>
    <TresPerspectiveCamera :position="[0, 3, 5]" :look-at="[0,0,0]"  />
    <TresMesh >
        <TresBoxGeometry :args="[1,1,1]" />
        <TresMeshBasicMaterial color="green" />
      </TresMesh>
  </TresCanvas>
</template>