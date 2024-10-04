<template>
    <h1>Home</h1>

    <div>
        <TresCanvas clear-color="#82DBC5" window-size>
            <TresPerspectiveCamera :args="[75, 1, 0.1, 1000]" :position="[3, 1, 4]" :look-at="[0, 0, 0]" />
            <OrbitControls />
            <TresMesh ref="torusRef" :position="[0, 0, 0]">
                <TresTorusKnotGeometry :args="[1,0.3,100,16]"/>
                <TresMeshNormalMaterial />
            </TresMesh>
            <TresAmbientLight :intensity="1" />
            <TresAxesHelper />
        </TresCanvas>
    </div>


</template>

<script lang="ts" setup>
import { TresCanvas, useRenderLoop } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';

const { onLoop } = useRenderLoop()
const torusRef = shallowRef()

onLoop(({ delta, elapsed }) => {
    if (torusRef.value) {
        torusRef.value.rotation.y += delta
        torusRef.value.rotation.z += delta

        torusRef.value.position.y = Math.sin(elapsed * 2)
    }
})

</script>

<style>
html,
body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
}

#app {
    height: 100%;
    width: 100%;
}
</style>
