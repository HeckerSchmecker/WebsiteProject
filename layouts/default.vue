<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <ul class="flex gap-4">
                    <li>
                        <NuxtLink to="/" class="font-bold">
                            Home
                        </NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/about">
                            About
                        </NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/projects" class="btn">
                            Projects
                        </NuxtLink>
                    </li>
                </ul>
            </nav>
        </header>

        <div class="container mx-auto p-4">
            <slot />
        </div>
    </div>
</template>

<script>
import { TresCanvas } from '@tresjs/core';
</script>

<style scoped>
.router-link-exact-active {
    color: #12b488;
}
</style>