<script setup lang="ts">
import { inject, ref } from 'vue'
import { type Client, type OptimizelyUserContext } from '@optimizely/optimizely-sdk'
import DecisionOutput from '../components/DecisionOutput.vue'
import Warning from '../components/WarningComponent.vue'
import { type Result } from '../types/Result'

const optimizelyClient = inject('optimizeClient') as Client

let projectId: string = ''
const datafile = optimizelyClient.getOptimizelyConfig()?.getDatafile();
if (datafile) {
  projectId = JSON.parse(datafile).projectId
}

const results: Result[] = []
for (let i = 0; i < 10; i++) {
  const userId = (Math.floor(Math.random() * (10000 - 1000) + 1000)).toString();

  const user = optimizelyClient.createUserContext(userId)

  const decision = user?.decide('product_sort')
  if (!decision) {
    continue
  }

  results.push({
    userId,
    variation: decision.variationKey,
    sortMethod: decision.variables['sort_method'],
  })
}
</script>

<template>
  <section class="run">
    <h1>Experiment Output</h1>
    <output v-if="results.length">
      <DecisionOutput v-for="result in results" :key="result.userId" :result="result" />
    </output>
    <Warning v-else>
      <p>
        No results found.
      </p>
      <p>Some reasons could include:</p>
      <ol>
        <li>Flag was off for everyone.</li>
        <li>Your sample size of visitors was too small. Rerun, or increase the iterations in the FOR loop.</li>
        <li>By default you have 2 keys for 2 project environments (dev/prod). Verify in Settings > Environments that you
          used the right key for the environment where your flag is toggled to ON.</li>
      </ol>
      <p>
        Check your key and project configuration on
        <a v-if="projectId !== ''"
          :href="'https://app.optimizely.com/v2/projects/' + projectId + '/settings/implementation'">settings page</a>
        <a v-else href="https://app.optimizely.com/v2/projects/">settings page</a>
      </p>
    </Warning>
  </section>
</template>

<style scoped>
@media (min-width: 1024px) {
  .run {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>
