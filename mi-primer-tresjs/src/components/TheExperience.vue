<script lang="ts" setup>
import { TresCanvas, vLog  } from '@tresjs/core'
</script>

<template>
  <TresCanvas window-size>
    <TresPerspectiveCamera v-log />
    <TresMesh v-log >
        <TresTorusGeometry :args="[1, 0.5, 16, 32]" />
        <TresMeshBasicMaterial color="orange" />
      </TresMesh>
  </TresCanvas>
</template>