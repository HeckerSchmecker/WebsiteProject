<template>
    <h1>Overview of my projects</h1>
    <ul>
        <li>
            <NuxtLink to="/projects/HVDC">
                Plant engineer at GE Vernova in HVDC projects
            </NuxtLink>
        </li>
        <li>
            <NuxtLink to="/projects/Drone">
                Drone Slalom Project at University
            </NuxtLink>
        </li>
    </ul>
</template>

<script setup>
    definePageMeta({
        layout: 'projects'
    })
</script>

<style scoped></style>