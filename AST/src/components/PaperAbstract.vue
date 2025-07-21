<template>
  <div class="abstract-section">
    <h2 class="section-title">Abstract</h2>
    <div class="abstract-content">
      <p>
        Transformer-based approaches have achieved promising performance in image restoration tasks,
        given their ability to model long-range dependencies, which is crucial for re covering clear
        images. Though diverse efficient attention mechanism designs have addressed the intensive
        compu tations associated with using transformers, they often in volve redundant information
        and noisy interactions from irrelevant regions by considering all available tokens. In this
        work, we propose an Adaptive Sparse Transformer (AST) to mitigate the noisy interactions of
        irrelevant areas and remove feature redundancy in both spatial and chan nel domains. AST
        comprises two core designs, i.e., an Adaptive Sparse Self-Attention (ASSA) block and a Fea
        ture Refinement Feed-forward Network (FRFN). Specifi cally, ASSA is adaptively computed
        using a two-branch paradigm, where the sparse branch is introduced to fil ter out the
        negative impacts of low query-key matching scores for aggregating features, while the dense
        one ensures sufficient information flow through the network for learn ing discriminative
        representations. Meanwhile, FRFN em ploys an enhance-and-ease scheme to eliminate feature re
        dundancy in channels, enhancing the restoration of clear latent images. Experimental results
        on commonly used benchmarks have demonstrated the versatility and compet itive performance
        of our method in several tasks, including rain streak removal, real haze removal, and
        raindrop re moval. The code and pre-trained models are available at
        https://github.com/joshyZhou/AST.
      </p>
    </div>
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
}

.abstract-content p {
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
