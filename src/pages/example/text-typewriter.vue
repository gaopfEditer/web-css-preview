<script lang="ts" setup>
const { data } = {data: '这是打字机效果'}
</script>

<template>
  <div class="typing-demo">
    <p class="content" :style="{ width: `${data?.length ?? 0}em` }">
      {{ data }}
    </p>
  </div>
</template>

<style scoped>
.typeing-demo {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.content {
  margin: 0 auto;
  overflow: hidden;
  font-size: 2em;
  white-space: nowrap;
  border-right: 2px solid;
  animation: typing 2s steps(20), blink 0.5s step-end infinite alternate;
}

@keyframes typing {
  from {
    width: 0;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}
</style>

<route lang="yaml">
name: text-打字机效果
meta:
  layout: demo
</route>
