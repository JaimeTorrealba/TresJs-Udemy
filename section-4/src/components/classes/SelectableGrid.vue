<script setup>
import { shallowRef } from 'vue'
import { DoubleSide, Vector3, SphereGeometry, Mesh, MeshBasicMaterial } from 'three';

const cursor = shallowRef(null)

const onSelect = (e) => {
    const cursorPos = new Vector3().copy(e.point).floor().addScalar(0.5)
    cursor.value.position.set(cursorPos.x, 0, cursorPos.z)
}

const createSphere = () => {
    const sphereGeometry = new SphereGeometry(0.5, 32, 32)
    const sphereMaterial = new MeshBasicMaterial({ color: 0x00ff00 })
    sphereMaterial.wireframe = true
    const sphere = new Mesh(sphereGeometry, sphereMaterial)

    sphere.position.copy(cursor.value.position)

    cursor.value.parent.add(sphere)
    
    console.log('jaime ~ createSphere ~ cursor.value.parent:', cursor.value.parent);
}
</script>
<template>
    <TresMesh ref="cursor" :position="[0.5, 0, 0.5]" :rotation-x="-Math.PI * 0.5">
        <TresPlaneGeometry :args="[1, 1]" />
        <TresMeshBasicMaterial :color="0xf7f7f7" :side="DoubleSide" />
    </TresMesh>
    <TresGridHelper :size="5" :divisions="10" />
    <TresMesh name="suelo" :rotation-x="-Math.PI * 0.5" :visible="false" 
    @pointer-move="e => onSelect(e)"
    @click="e => createSphere(e)"
    >
        <TresPlaneGeometry :args="[10, 10, 32]" />
        <TresMeshBasicMaterial :color="0xf7f7f7" :side="DoubleSide" />
    </TresMesh>
</template>