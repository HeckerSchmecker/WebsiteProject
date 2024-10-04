<template>
    <div>
        <h2>Plant engineer at GE Vernova in HVDC projects</h2>
        <p>Salzbergen in Germany and Villeurbanne in France</p>
    </div>
    <div>
        <HvdcModel />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'projects'
})

import { TresCanvas, useRenderLoop } from '@tresjs/core';

const { onLoop } = useRenderLoop()
const cubeRef = shallowRef()

onLoop(({ delta, elapsed }) => {
    if (cubeRef.value) {
        cubeRef.value.rotation.y += delta
        cubeRef.value.rotation.z += delta

        cubeRef.value.position.y = Math.sin(elapsed * 2)
    }
})
</script>

<style lang="scss" scoped></style>