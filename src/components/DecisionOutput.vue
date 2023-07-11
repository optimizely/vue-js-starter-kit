<script setup lang="ts">
import { type Result } from '../types/Result'

const props = defineProps({
  result: Result
})
</script>

<template>
    <pre>
        User 
        {{ result.userId }} saw variation
        {{ result.variation }} and got products sorted by 
        {{ result.sortMethod }}
    </pre>
</template>

<style scoped>
pre {
    margin: 0px;
}
</style>