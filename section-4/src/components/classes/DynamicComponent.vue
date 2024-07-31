<script setup lang="ts">
import { ref } from 'vue'
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import { gsap } from 'gsap'
import Box from './componentsClass/TheBox.vue'
import Sphere from './componentsClass/TheSphere.vue'
import Cone from './componentsClass/TheCone.vue'


const components = {
    Box,
    Sphere,
    Cone
}

const current = ref('Sphere')

const handleComponent = (component) => {
    current.value = component
}

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
    <div class="show-box">
        <button @click="handleComponent('Box')">Toggle Box</button>
        <button @click="handleComponent('Sphere')">Toggle Sphere</button>
        <button @click="handleComponent('Cone')">Toggle Cone</button>
    </div>
    <TresCanvas clear-color="#333" window-size>
        <TresPerspectiveCamera :position="[0, 10, 10]" :look-at="[0, 0, 0]" />
        <!-- <Transition @enter="onEnter" @leave="onLeave" :css="false"> -->
        <component :is="components[current]" />
        <!-- </Transition> -->
        <OrbitControls />
    </TresCanvas>
</template>
<style scoped>
.show-box {
    position: absolute;
    top: 0;
    left: 40%;
    z-index: 100;
    padding: 10px;
    background: #333;
    color: white;
    border: none;
    cursor: pointer;
}
</style>