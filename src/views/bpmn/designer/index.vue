<template>
  <section class='Designer'>
    <div id="bpmcanvas"></div>
  </section>
</template>

<script setup lang='ts'>
import BpmnViewer from 'bpmn-js';
import xml from './flow.xml'
const bpmModeler = ref()
const init = () => {
  bpmModeler.value = new BpmnViewer({
    container: '#bpmcanvas'
  })
  createNewDiagram()
}
const createNewDiagram = () => {
  console.log("xml", xml)
  // bpmModeler.value.importXML(xml, (err) => {
  //   if (err) {
  //     console.error('加载失败')
  //   } else {
  //     console.log('加载成功')
  //   }
  // })
}
onMounted(() => {
  init()
})
</script>
<style scoped lang='scss'>
.Designer {
  flex: 1;
  padding: 20px;
}
</style>