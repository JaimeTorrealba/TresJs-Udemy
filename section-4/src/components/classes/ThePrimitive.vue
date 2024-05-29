<script setup>
import { TeapotGeometry } from 'three/addons/geometries/TeapotGeometry.js';
import { MeshBasicMaterial, Mesh } from 'three';

const geometry = new TeapotGeometry(2);
const material = new MeshBasicMaterial({ color: 0x00ff00 });
const teapot = new Mesh(geometry, material);

</script>
<template>
    <TresMesh :geometry="geometry" :material="material">

    </TresMesh>
</template>