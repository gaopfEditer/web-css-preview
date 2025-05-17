<script lang="ts" setup>
const { data } = {data: "这是一串特别长的文本文本文本文本文本文本文本文本文本文本"}
</script>

<template>
  <div>
    <p class="content">
      {{ data }}
    </p>
  </div>
</template>

<style scoped>
.content {
  width: 10em;
  margin: 0 auto;
  font-size: 2em;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
</style>

<route lang="yaml">
name: text-文本省略
meta:
  layout: demo
</route>
