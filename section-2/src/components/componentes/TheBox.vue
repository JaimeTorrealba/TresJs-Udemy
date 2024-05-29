<script setup>
import { shallowRef } from 'vue'
import { useTresContext, useLoop } from '@tresjs/core'
import { Stats } from '@tresjs/cientos'

const boxRef = shallowRef()

const {onBeforeRender } = useLoop()

onBeforeRender(({delta}) => {
  console.log('onBeforeRender')

  // boxRef.value.rotation.x += 0.01
   boxRef.value.rotation.y += delta
}, -1)

</script>
<template>
  <Stats />
    <TresMesh ref="boxRef">
        <TresBoxGeometry :args="[1,1,1]" />
        <TresMeshBasicMaterial color="green" />
      </TresMesh>
</template>