<script setup>
import { Sky, Ocean, useGLTF, useAnimations } from '@tresjs/cientos'


const path = '/models/scifi_drone_1.1.glb'
const { scene, animations } = await useGLTF(path)

const { actions } = useAnimations(animations, scene)

const currentAction = actions["Armature|idle"]

currentAction.play()
</script>
<template>
    <primitive :position-y="2" :rotation-y="Math.PI" :scale="0.01" :object="scene" />
    <Ocean :position-y="-2" />
    <Sky />
</template>