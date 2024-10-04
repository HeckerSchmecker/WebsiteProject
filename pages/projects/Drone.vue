<template>
    <div>
        <h2>Drone slalom</h2>
        <p>University of Bayreuth 2022</p>
    </div>
    <div>
        <DroneModel />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'projects'
})

import { TresCanvas, useRenderLoop } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';
import {useGLTF} from '@tresjs/cientos'

const { onLoop } = useRenderLoop()
const torusRef = shallowRef()

const {scene: model } = await useGLTF('/compressed_nova_map.glb', {draco: true})

onLoop(({ delta, elapsed }) => {
    if (torusRef.value) {
        torusRef.value.rotation.y += delta
        torusRef.value.rotation.z += delta

        torusRef.value.position.y = Math.sin(elapsed * 2)
    }
})
</script>

<style lang="scss" scoped></style>