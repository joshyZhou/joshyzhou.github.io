<template>
  <div class="paper-container">
    <!-- 第一个模块：标题和作者信息 -->
    <PaperHeader />

    <!-- 第二个模块：摘要 -->
    <PaperAbstract />

    <!-- 第三个模块：方法 -->
    <PaperMethod />

    <!-- 第四个模块：实验 -->
    <PaperExperiments />
  </div>
</template>

<script setup lang="ts">
import PaperHeader from './PaperHeader.vue'
import PaperAbstract from './PaperAbstract.vue'
import PaperMethod from './PaperMethod.vue'
import PaperExperiments from './PaperExperiments.vue'
</script>

<style scoped>
.paper-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 40px 20px;
  background: #f5f5f5;
  min-height: 100vh;
}

@media (max-width: 768px) {
  .paper-container {
    padding: 20px 15px;
  }
}
</style>
