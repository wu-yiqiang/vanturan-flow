<script setup lang="ts">
import type { ParallelNode } from './type'
import GatewayNode from './GatewayNode.vue'

defineProps<{
  node: ParallelNode
}>()
</script>

<template>
  <GatewayNode v-bind="$attrs" :node="node">
    <template #default="{ addNode, readOnly }">
      <el-button type="primary" :disabled="readOnly" @click="addNode('condition', node)" plain round
        >添加并行节点</el-button
      >
    </template>
  </GatewayNode>
</template>

<style scoped lang="scss"></style>
