<script lang="ts" setup>
// import { shallowRef, watch } from 'vue'
import { TresCanvas  } from '@tresjs/core'
import TheBox from './componentes/TheBox.vue'

</script>

<template>
  <TresCanvas window-size>
    <TresPerspectiveCamera :position="[0, 3, 5]" :look-at="[0,0,0]"  />
    <TheBox />
  </TresCanvas>
</template>