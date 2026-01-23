<template>
  <section class='Pannel'>
    <ButtonTab :tabs="tabs" activeKey="class1" >
      <template #class1>
        class1
      </template>
       <template #class2>
        class2
      </template>
      <template #class3>
        class3
      </template>
      <template #class4>
        class4
      </template>
    </ButtonTab>
  </section>
</template>

<script setup lang='ts'>
import ButtonTab from '@/components/ButtonTab/index.vue'
const tabs = [
  {label: '分类1', value: 'class1' },
  {label: '分类2', value: 'class2'},
  {label: '分类3', value: 'class3'},
  {label: '分类4', value: 'class4'},
]
</script>
<style scoped lang='scss'>
.Pannel {
  padding: 20px;
  width: fit-content;
  width: 400px;
  background-color: white;
  overflow: auto;
  border-radius: 4px;
}
</style>