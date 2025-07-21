<template>
  <div class="method-section">
    <h2 class="section-title">Method</h2>

    <!-- 架构图 -->
    <div class="architecture-diagram">
      <img src="/hint-architecture.png" alt="HINT Architecture Diagram" class="diagram-image" />
      <p class="image-caption">
        Illustration of the proposed Hierarchical multi-head atteNtion driven Transformer model
        (HINT). (a) Overview architecture of the proposed HINT. (b) Hierarchical Multi-Head
        Attention (HMHA) mechanism.
      </p>
    </div>

    <!-- 方法介绍 -->
    <div class="method-content">
      <div class="overview-section">
        <p class="introduction">
          We propose <strong>HINT (Hierarchical multi-head atteNtion driven Transformer)</strong>, a
          Transformer model designed for image restoration that addresses the
          <strong>redundancy issue</strong>
          in standard Multi-Head Attention (MHA). In conventional Transformers, different attention
          heads often focus on the same image regions, limiting the model's ability to capture
          diverse features. HINT explores diverse learners and enhances interactions between
          attention heads to overcome this limitation.
        </p>

        <p class="core-components">
          The HINT model is built upon two key modules:
          <strong>Hierarchical Multi-Head Attention (HMHA)</strong> and the
          <strong>Query-Key Cache Updating (QKCU)</strong> mechanism, which work together to enable
          diverse feature learning and enhanced head collaboration.
        </p>
      </div>

      <!-- 核心组件展示区 -->
      <div class="components-showcase">
        <div class="component-card main-architecture">
          <h3 class="card-title">Architecture Overview</h3>
          <p>
            The HINT model follows an encoder-decoder architecture with N-level processing. A
            convolutional layer first extracts shallow features, which are processed through
            encoder-decoder blocks with skip connections. The encoder contains FFN blocks, while the
            decoder integrates both HMHA and FFN modules. A final refinement stage with
            convolutional layers generates the restored image.
          </p>
        </div>

        <div class="component-card modulation-details">
          <h3 class="card-title">QKCU Modulation Mechanisms</h3>
          <div class="modulation-image-container">
            <img
              src="/modulation-details.png"
              alt="Intra and Inter Modulation Details"
              class="modulation-image"
            />
            <p class="image-caption">
              Detailed structure of (a) Intra Modulation and (b) Inter Modulation mechanisms
            </p>
          </div>
          <div class="modulation-description">
            <div class="modulation-item">
              <strong>Intra-Layer Modulation (IntraCache):</strong> Functions as a gating module
              within a single layer, using GELU activation and element-wise operations to
              selectively enhance informative elements from aggregated attention head features.
            </div>
            <div class="modulation-item">
              <strong>Inter-Layer Modulation (InterCache):</strong> Modulates attention scores using
              historical attention information across layers, computing shift and scale components
              to dynamically modify attention with progressive cache updating controlled by
              hyperparameter α.
            </div>
          </div>
        </div>
      </div>

      <!-- 技术特性网格 -->
      <div class="features-grid">
        <div class="feature-item">
          <h4>Hierarchical Multi-Head Attention (HMHA)</h4>
          <p>
            Employs reranking and hierarchical channel splitting to create diverse subspaces (C₁ ≤
            C₂ ≤ ... ≤ Cₙ), enabling attention heads to act as diverse learners capturing
            distinctive contextual features
          </p>
        </div>

        <div class="feature-item">
          <h4>Query-Key Cache Updating (QKCU)</h4>
          <p>
            Enhances collaboration between attention heads through intra-layer and inter-layer
            modulation schemes, using cached attention information to improve feature interactions
          </p>
        </div>

        <div class="feature-item">
          <h4>Redundancy Mitigation</h4>
          <p>
            Addresses the core problem where standard MHA heads focus on similar regions, ensuring
            each subspace contains independent information through channel similarity-based
            reranking
          </p>
        </div>

        <div class="feature-item">
          <h4>Progressive Cache Updating</h4>
          <p>
            Inter-layer cache mechanism progressively updates across layers using hyperparameter α
            control, enabling dynamic attention score modulation based on historical information
          </p>
        </div>
      </div>
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
}

.overview-section {
  background: #f8f9fa;
  padding: 30px;
  border-radius: 8px;
  margin-bottom: 40px;
  border: 1px solid #dee2e6;
}

.introduction,
.core-components {
  margin-bottom: 20px;
  text-align: justify;
}

.components-showcase {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
  margin-bottom: 40px;
}

.component-card {
  background: white;
  border-radius: 8px;
  padding: 25px;
  border: 1px solid #dee2e6;
}

.card-title {
  font-size: 18px;
  font-weight: bold;
  color: #2c3e50;
  margin: 0 0 15px 0;
  padding-bottom: 8px;
  border-bottom: 1px solid #dee2e6;
}

.main-architecture p {
  text-align: justify;
  margin: 0;
}

.modulation-details {
  position: relative;
}

.modulation-image-container {
  text-align: center;
  margin-bottom: 20px;
}

.modulation-image {
  max-width: 100%;
  height: auto;
  border-radius: 4px;
  border: 1px solid #dee2e6;
}

.modulation-description {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.modulation-item {
  padding: 15px;
  background: #f8f9fa;
  border-radius: 4px;
  font-size: 14px;
  line-height: 1.5;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  margin-top: 30px;
}

.feature-item {
  padding: 20px;
  background: white;
  border-radius: 8px;
  border: 1px solid #dee2e6;
}

.feature-item h4 {
  font-size: 16px;
  font-weight: bold;
  color: #2c3e50;
  margin: 0 0 12px 0;
  line-height: 1.3;
}

.feature-item p {
  font-size: 14px;
  color: #495057;
  margin: 0;
  line-height: 1.5;
  text-align: justify;
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

  .overview-section {
    padding: 20px;
    margin-bottom: 30px;
  }

  .components-showcase {
    grid-template-columns: 1fr;
    gap: 20px;
    margin-bottom: 30px;
  }

  .component-card {
    padding: 20px;
  }

  .card-title {
    font-size: 18px;
  }

  .modulation-item {
    font-size: 13px;
    padding: 10px;
  }

  .features-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }

  .feature-item {
    padding: 15px;
  }

  .method-content {
    font-size: 14px;
  }

  .introduction,
  .core-components {
    text-align: left;
  }
}
</style>
