<script setup>
import { reactive } from 'vue';
import {Pane} from 'tweakpane';

const pane = new Pane();

const object = reactive({
    x: 0,
    width: 1
    // y: 0,
    // z: 0
});

pane.addBinding(object, 'x', {
    min: -10,
    max: 10,
    step: 1,
});
pane.addBinding(object, 'width', {
    min: -10,
    max: 10,
    step: 0.1,
});
</script>
<template>
<TresMesh :position="[object.x, 0, 0]">
    <TresBoxGeometry :args="[object.width, 1, 1]" />
    <TresMeshNormalMaterial  />
</TresMesh>
</template>