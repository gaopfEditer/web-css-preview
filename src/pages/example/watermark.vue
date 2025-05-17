<script lang="ts" setup>
import WaterMark from '~/assets/js/waterMark'

const waterMark = new WaterMark({ watermark_txt: 'kuizuo' })
onMounted(() => {
  waterMark.init()
})

onBeforeUnmount(() => {
  waterMark.destory()
})
</script>

<template>
  <div >222222222222</div>
</template>

<style scoped>
</style>

<route lang="yaml">
name: text-水印
meta:
  layout: demo
</route>
