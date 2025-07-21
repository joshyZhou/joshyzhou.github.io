<template>
  <div class="abstract-section">
    <h2 class="section-title">Abstract</h2>
    <p class="abstract-content">
      Transformer-based approaches have gained significant attention in image restoration, where the
      core component, i.e, Multi-Head Attention (MHA), plays a crucial role in capturing diverse
      features and recovering high-quality results. In MHA, heads perform attention calculation
      independently from uniform split subspaces, and a redundancy issue is triggered to hinder the
      model from achieving satisfactory outputs. In this paper, we propose to improve MHA by
      exploring diverse learners and introducing various interactions between heads, which results
      in a Hierarchical multIhead atteNtion driven Transformer model, termed HINT, for image
      restoration. HINT contains two modules, i.e., the Hierarchical Multi-Head Attention (HMHA) and
      the QueryKey Cache Updating (QKCU) module, to address the redundancy problem that is rooted in
      vanilla MHA. Specifically, HMHA extracts diverse contextual features by employing heads to
      learn from subspaces of varying sizes and containing different information. Moreover, QKCU,
      comprising intra- and inter-layer schemes, further reduces the redundancy problem by
      facilitating enhanced interactions between attention heads within and across layers. Extensive
      experiments are conducted on 12 benchmarks across 5 image restoration tasks, including
      low-light enhancement, dehazing, desnowing, denoising, and deraining, to demonstrate the
      superiority of HINT.
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
