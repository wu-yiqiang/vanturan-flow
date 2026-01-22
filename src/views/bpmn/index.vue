<template>
  <section class='Bpmn'>
    <Topbar />
    <div class="main-box">
        <Designer />
        <Pannel />
    </div>
  </section>
</template>

<script setup lang='ts'>
import Topbar from './topbar/index.vue'
import Pannel from './pannel/index.vue'
import Designer from './designer/index.vue'
</script>
<style scoped lang='scss'>
.Bpmn {
    // height: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    .main-box {
      flex: 1;
      display: flex;
      justify-content: space-between;
    }
}
</style>