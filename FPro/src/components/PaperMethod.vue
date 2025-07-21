<template>
  <div class="method-section">
    <h2 class="section-title">Method</h2>

    <!-- 架构图 -->
    <div class="architecture-diagram">
      <img src="/method-architecture.png" alt="FPro Architecture Diagram" class="diagram-image" />
    </div>

    <!-- 方法介绍 -->
    <div class="method-content">
      <p class="introduction">
        We propose a <strong>Frequency Prompt Guided Transformer (FPro)</strong>, an innovative
        approach for image restoration that leverages frequency domain information to guide the
        restoration process. The core innovation lies in using frequency prompts to help the model
        "see the unseen" degradation patterns that are difficult to perceive in the spatial domain.
      </p>

      <p class="core-components">
        The FPro model introduces several novel components including a
        <strong>Dual Prompt Block (DPB)</strong> that processes both low-frequency and
        high-frequency information, along with specialized modules for frequency-aware feature
        processing.
      </p>

      <h3 class="subsection-title">Overview of the Proposed FPro</h3>
      <p>
        Except for the common upper restoration branch, which is similar to existing methods, FPro
        contains another bottom prompt branch to extract informative features from a frequency
        perspective. Specifically, the primary components of the prompt branch in this framework are
        the <strong>Gated Dynamic Decoupler (GDD)</strong> and
        <strong>Dual Prompt Block (DPB)</strong>.
      </p>

      <h3 class="subsection-title">Gated Dynamic Decoupler (GDD)</h3>
      <div class="module-diagram">
        <img src="/gdd-module.png" alt="Gated Dynamic Decoupler Module" class="module-image" />
      </div>
      <p>
        The GDD is employed to decompose the low-frequency components and corresponding
        high-frequency characteristics from the input features. This module serves as the foundation
        for frequency-aware processing by separating different frequency bands using a gating
        mechanism that controls the decomposition process.
      </p>

      <h3 class="subsection-title">Dual Prompt Block (DPB)</h3>
      <div class="module-diagram">
        <img
          src="/hpm-lpm-modules.png"
          alt="High-frequency and Low-frequency Prompt Modulators"
          class="module-image"
        />
        <p class="image-caption">
          Illustrations of the proposed components. (a) High-frequency Prompt Modulator (HPM); (b)
          Low-frequency Prompt Modulator (LPM)
        </p>
      </div>
      <p>
        These frequency-specific features are further processed in DPB, which consists of two
        specialized modulators:
      </p>
      <p>
        <strong>High-frequency Prompt Modulator (HPM):</strong> Processes high-frequency
        characteristics to generate representative high-frequency prompts that help identify and
        restore fine details and edges.
      </p>
      <p>
        <strong>Low-frequency Prompt Modulator (LPM):</strong> Handles low-frequency components to
        generate low-frequency prompts that guide the restoration of overall structure and smooth
        regions.
      </p>

      <h3 class="subsection-title">Frequency Prompt Integration</h3>
      <p>
        The generated representative frequency prompts facilitate clear image reconstruction by
        providing frequency-specific guidance to the restoration process. This allows the model to
        "see the unseen" degradation patterns that are difficult to perceive in the spatial domain
        alone. Standard transformer components (MSA & FFN) are integrated to capture long-range
        dependencies and perform feature transformation, working in conjunction with the
        frequency-specific prompts.
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
// Method component with architecture diagram
</script>

<style scoped>
/* .method-section 样式由 App.vue 中的全局样式控制 */

.section-title {
  font-size: 32px;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 30px;
  text-align: center;
  font-family: 'Times New Roman', serif;
}

.architecture-diagram {
  text-align: center;
  margin: 30px 0;
}

.diagram-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.method-content {
  font-size: 16px;
  line-height: 1.7;
  color: #444;
  text-align: justify;
}

.introduction,
.core-components {
  margin-bottom: 25px;
}

.subsection-title {
  font-size: 24px;
  font-weight: bold;
  color: #34495e;
  margin: 35px 0 20px 0;
  padding-bottom: 8px;
}

.pipeline-steps {
  margin: 20px 0;
}

.step {
  margin-bottom: 25px;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
}

.step h4 {
  font-size: 18px;
  font-weight: bold;
  color: #2c3e50;
  margin: 0 0 10px 0;
}

.sub-components {
  margin-top: 15px;
}

.component {
  margin: 10px 0;
  padding: 15px;
  background: white;
  border-radius: 6px;
}

.core-modules {
  margin: 20px 0;
}

.module {
  margin-bottom: 30px;
  padding: 25px;
  background: #f8f9fa;
  border-radius: 10px;
}

.module-diagram {
  text-align: center;
  margin: 20px 0;
}

.module-image {
  max-width: 90%;
  height: auto;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  border: 1px solid #e9ecef;
}

.image-caption {
  font-size: 14px;
  color: #666;
  font-style: italic;
  margin-top: 10px;
  line-height: 1.4;
}

.module h4 {
  font-size: 20px;
  font-weight: bold;
  color: #2c3e50;
  margin: 0 0 15px 0;
}

.module-details {
  margin-top: 15px;
}

.detail {
  margin: 15px 0;
  padding: 15px;
  background: white;
  border-radius: 6px;
}

.detail ul {
  margin: 10px 0;
  padding-left: 20px;
}

.detail li {
  margin: 8px 0;
}

strong {
  color: #2c3e50;
}

em {
  font-style: italic;
  color: #555;
}

@media (max-width: 768px) {
  .method-section {
    padding: 30px 20px;
  }

  .section-title {
    font-size: 24px;
  }

  .subsection-title {
    font-size: 20px;
  }

  .method-content {
    font-size: 14px;
  }

  .step,
  .module {
    padding: 15px;
  }
}
</style>
