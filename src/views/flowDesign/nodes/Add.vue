<script setup lang="ts">
import type { PopoverInstance } from 'element-plus'
import type { NodeType } from './type'
import type { Ref } from 'vue'

const { readOnly } = inject<{
  readOnly?: Ref<boolean>
}>('flowDesign', { readOnly: ref(false) })
const popoverRef = ref<PopoverInstance>()
const $emits = defineEmits<{
  (e: 'addNode', type: NodeType): void
}>()
const addApprovalNode = () => {
  $emits('addNode', 'approval')
  popoverRef.value?.hide()
}
const addCcNode = () => {
  $emits('addNode', 'cc')
  popoverRef.value?.hide()
}
const addExclusiveNode = () => {
  $emits('addNode', 'exclusive')
  popoverRef.value?.hide()
}
const addTimerNode = () => {
  $emits('addNode', 'timer')
  popoverRef.value?.hide()
}
const addNotifyNode = () => {
  $emits('addNode', 'notify')
  popoverRef.value?.hide()
}
const addServiceNode = () => {
  $emits('addNode', 'service')
  popoverRef.value?.hide()
}
const addScriptNode = () => {
  $emits('addNode', 'script')
  popoverRef.value?.hide()
}
const addParallelNode = () => {
   $emits('addNode', 'parallel')
  popoverRef.value?.hide()
}
const nodeLists = [
  { label: '审批人', icon: "el:Stamp", bgColor: '#ff943e', event: addApprovalNode },
  { label: '抄送人', icon: "el:Promotion", bgColor: '#3296fa', event: addCcNode },
  { label: '互斥分支', icon: "el:Share", bgColor: '#45cf9b', event: addExclusiveNode },
  { label: '并行分支', icon: "Parallels", bgColor: '#4fd3b4', event: addParallelNode },
  { label: '计时等待', icon: "el:Timer", bgColor: '#e872b7', event: addTimerNode },
  { label: '消息通知', icon: "el:BellFilled", bgColor: '#95d475', event: addNotifyNode },
  { label: '服务节点', icon: "el:Tools", bgColor: '#ffc107', event: addServiceNode },
  { label: '脚本节点', icon: "Scripts", bgColor: '#eebc41', event: addScriptNode },
]
</script>

<template>
  <div class="add-but">
    <el-popover
      placement="bottom-start"
      ref="popoverRef"
      trigger="click"
      title="添加节点"
      :width="336"
    >
      <el-space wrap>
        <div v-for="(node, index) in nodeLists" :key="index" class="node-select" @click="node.event()">
          <div :style="{backgroundColor: node?.bgColor}" class="icons">
            <svg-icon :name="node?.icon" />
          </div>
          <el-text>{{ node?.label }}</el-text>
        </div>
      </el-space>
      <template #reference>
        <el-button
          v-show="!readOnly"
          icon="Plus"
          type="primary"
          style="z-index: 1"
          circle
        ></el-button>
      </template>
    </el-popover>
  </div>
</template>

<style scoped lang="scss">
.node-select {
  cursor: pointer;
  display: flex;
  padding: 8px;
  width: 135px;
  border-radius: 10px;
  position: relative;
  background-color: var(--el-fill-color-light);

  &:hover {
    background-color: var(--el-color-primary-light-9);
    box-shadow: var(--el-box-shadow-light);
    color: var(--el-color-primary);
  }
  .icons {
    border-radius: 50%;
    display: grid;
    place-content: center;
     .svg-icon {
    font-size: 25px;
    padding: 5px;
    border-radius: 50%;
    color: var(--el-color-white);

   
  }


  }
    .el-text {
    margin-left: 10px;
  }
 
}

.add-but {
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 20px 0 32px;
  position: relative;

  &:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    width: 1px;
    height: 100%;
    background-color: var(--el-border-color);
  }
}
</style>
