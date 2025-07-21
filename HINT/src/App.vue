<script setup lang="ts">
import PaperHeader from './components/PaperHeader.vue'
import PaperAbstract from './components/PaperAbstract.vue'
import PaperMethod from './components/PaperMethod.vue'
import PaperExperiments from './components/PaperExperiments.vue'
import PaperApplication from './components/PaperApplication.vue'
</script>

<template>
  <PaperHeader />

  <PaperAbstract />

  <PaperMethod />

  <PaperExperiments />

  <PaperApplication />
</template>

<style>
body {
  margin: 0;
  padding: 0;
  background: white;
}

#app {
  display: flex !important;
  flex-direction: column !important;
  width: 100%;
  align-items: center;
  background: white;
  min-height: 100vh;
}

/* 确保所有组件都是块级元素并占满宽度 */
.paper-header,
.abstract-section,
.method-section,
.experiments-section,
.application-section {
  display: block !important;
  width: 98% !important;
  max-width: 1200px !important;
  box-sizing: border-box !important;
  clear: both !important;
  float: none !important;
  margin-left: auto !important;
  margin-right: auto !important;
  background: white;
  border-radius: 15px;
  box-shadow: 0 0px 12px rgba(0, 0, 0, 0.4);
  margin-bottom: 25px;
  padding: 40px;
  border: 1px solid #e0e0e0;
}

/* 第一个模块特殊样式 */
.paper-header {
  margin-top: 40px;
}

/* 强制垂直布局，防止任何并排显示 */
* {
  flex-shrink: 0;
}
</style>
