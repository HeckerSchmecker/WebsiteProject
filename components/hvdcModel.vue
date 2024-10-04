<template>
    <div>
        <TresCanvas clear-color="#82DBC5" window-size>
            <TresPerspectiveCamera :args="[75, 1, 0.1, 1000]" :position="[3, 1, 4]" :look-at="[0, 0, 0]" />
            <OrbitControls :damping-factor="0.1" :enable-damping="true" />
            <primitive :object="model" />
            <TresAmbientLight :intensity="1" />
        </TresCanvas>
    </div>
    <h3>Replace this with HVDC Model</h3>
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