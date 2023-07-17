<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import GetStartedIcon from './icons/IconGetStarted.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Quick Start Documentation</template>

    We'll be following much of the
    <a
      href="https://docs.developers.optimizely.com/feature-experimentation/docs/javascript-browser-quickstart"
      target="_blank"
      rel="noopener"
      >Optimizely Javascript quick start documentation</a
    >
    as a basis for this example app.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Tooling</template>

    <p>
      We've created this project using the standard Vue tooling and wrapped it in a
      <a href="https://containers.dev/" target="_blank" rel="noopener">Dev Container</a>
      for use with VS Code.
    </p>

    <p>
      More instructions are available in
      <code>README</code>
      document.
    </p>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <GetStartedIcon />
    </template>
    <template #heading>Get Started</template>

    <p>
      If you're using your own Optimizely SDK key, you can edit it to the
      <code>src/App.vue</code>. Then, click the Run nav link 👈 to see the example in action.
    </p>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Optimizely Support</template>

    If you have any qusetions about implementing Feature Experimentation, reach out to your
    Optimizely representative. You can also check out the the
    <a
      href="https://docs.developers.optimizely.com/feature-experimentation/docs"
      target="_blank"
      rel="noopener"
      >SDK documentation</a
    >
    or GOTO our
    <a href="https://support.optimizely.com/hc/en-us" target="_blank" rel="noopener">support site</a
    >.
  </WelcomeItem>
</template>
