<template>
  <section class='Designer'>
    <div ref="bpmncanvas" id="bpmncanvas" class="bpmncanvas"></div>
    <section class='Palette' id="Palette"></section>
  </section>
</template>

<script setup lang='ts'>
import BpmnModeler from 'bpmn-js/lib/Modeler'
import propertiesProviderModule from 'bpmn-js-properties-panel/lib/provider/camunda'
import BpmnViewer from 'bpmn-js';
import { xmlStr } from './datas';
const bpmModeler = ref()
const bpmncanvas = ref()
const init = () => {
  bpmModeler.value = new BpmnModeler({
    container: bpmncanvas.value,
    propertiesPanel: {
        parent: '#Palette'
      },
      additionalModules: [
        // propertiesProviderModule
      ]
  })
  createNewDiagram()
}
const createNewDiagram = () => {
  bpmModeler.value.importXML(xmlStr, (err: any) => {
    if (err) {
      console.error('加载失败')
    } else {
      console.log('加载成功')
    }
  })
}
onMounted(() => {
 init()
})
</script>
<style scoped lang='scss'>
.Designer {
  flex: 1;
  .bpmncanvas {
    height: 100%;
    background-color: #f3f3f3;
    border-radius: 6px;
    :focus {
      border: none !important;
      outline: none !important;
    }
  }
}
</style>