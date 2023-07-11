<script setup lang="ts">
import { defineProps } from 'vue'
import { type Result } from '../types/Result'

const props = defineProps({
  result: {
    type: Object as () => Result,
    required: true
  }
})
</script>

<template>
    <div>        
        User 
        <b class="userId">{{ result.userId }}</b> saw variation
        <b class="variation">{{ result.variation }}</b> and got products sorted by 
        <b class="sortMethod">{{ result.sortMethod }}</b>
    </div>
</template>

<style scoped>
div {
    margin: 0px;
    font-family: monospace;
}
b {
    font-weight: bold;
}
.userId {
    color: #FC7F10;
}
.variation {
    color: #861DFF;
}
.sortMethod {
    color: #00CCFF;
}
</style>