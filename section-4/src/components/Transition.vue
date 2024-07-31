<script setup lang="ts">
import { ref } from 'vue'
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import { gsap } from 'gsap'

const showBox = ref(false)

const onEnter = (el, done) => {
    gsap.from(el.material, { duration: 1, opacity: 0, onComplete: done })
    gsap.from(el.position, { duration: 1, y: -1 })
}
const onLeave = (el, done) => {
    gsap.to(el.material, { duration: 1, opacity: 0 })
    gsap.to(el.position, { duration: 1, y: -1 })
}
</script>

<template>
    <button class="show-box" @click="showBox = !showBox">Toggle Box</button>
    <TresCanvas clear-color="#333" window-size>
        <TresPerspectiveCamera :position="[0, 10, 10]" :look-at="[0, 0, 0]" />
        <Transition @enter="onEnter" @leave="onLeave" :css="false">
            <TresMesh v-if="showBox">
                <TresBoxGeometry :args="[1, 1, 1]" />
                <TresMeshNormalMaterial transparent />
            </TresMesh>
        </Transition>
        <OrbitControls />
    </TresCanvas>
</template>
<style scoped>
.show-box {
    position: absolute;
    top: 0;
    left: 50%;
    z-index: 100;
    padding: 10px;
    background: #333;
    color: white;
    border: none;
    cursor: pointer;
}
</style>