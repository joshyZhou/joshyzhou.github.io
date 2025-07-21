<template>
  <div class="abstract-section">
    <h2 class="section-title">Abstract</h2>
    <p class="abstract-content">
      How to explore useful features from images as prompts to guide the deep image restoration
      models is an effective way to solve im age restoration. In contrast to mining spatial
      relations within images as prompt, which leads to characteristics of different frequencies
      being neglected and further remaining subtle or undetectable artifacts in the restored image,
      we develop a Frequency Prompting image restoration method, dubbed FPro, which can effectively
      provide prompt compo nents from a frequency perspective to guild the restoration model address
      these differences. Specifically, we first decompose input features into sep arate frequency
      parts via dynamically learned filters, where we introduce a gating mechanism for suppressing
      the less informative elements within the kernels. To propagate useful frequency information as
      prompt, we then propose a dual prompt block, consisting of a low-frequency prompt modulator
      (LPM) and a high-frequency prompt modulator (HPM), to handle signals from different bands
      respectively. Each modulator con tains a generation process to incorporate prompting
      components into the extracted frequency maps, and a modulation part that modifies the prompt
      feature with the guidance of the decoder features. Experimental results on commonly used
      benchmarks have demonstrated the favorable performance of our pipeline against SOTA methods on
      5 image restora tion tasks, including deraining, deraindrop, demoiréing, deblurring, and
      dehazing. The source code and pre-trained models will be available at
      https://github.com/joshyZhou/FPro.
    </p>
  </div>
</template>

<script setup lang="ts">
// No props or reactive data needed for this static content
</script>

<style scoped>
/* .abstract-section 样式由 App.vue 中的全局样式控制 */

.section-title {
  font-size: 32px;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 25px;
  text-align: center;
  font-family: 'Times New Roman', serif;
}

.abstract-content {
  background: #f8f9fa;
  padding: 35px;
  border-radius: 10px;
  font-size: 18px;
  text-align: justify;
  line-height: 1.8;
  color: #444;
  font-family: 'Times New Roman', serif;
  margin: 0;
}

.highlight {
  color: #e74c3c;
  font-weight: bold;
}

@media (max-width: 768px) {
  .abstract-section {
    padding: 20px;
  }

  .section-title {
    font-size: 24px;
  }

  .abstract-content {
    padding: 20px;
    font-size: 15px;
    text-align: left;
  }
}
</style>
