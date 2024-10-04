<template>
    <div>
        <h2>Plant engineer at GE Vernova in HVDC projects</h2>
        <p>Salzbergen in Germany and Villeurbanne in France</p>
    </div>
    <div>
        <TresCanvas clear-color="#82DBC5" window-size>
            <TresPerspectiveCamera :position="[3, 3, 3]" :look-at="[0, 0, 0]" />
            <TresMesh ref="cubeRef" :position="[0, 0, 0]">
                <TresBoxGeometry />
                <TresMeshNormalMaterial />
            </TresMesh>
            <TresAmbientLight :intensity="1" />
            <TresAxesHelper />
        </TresCanvas>
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