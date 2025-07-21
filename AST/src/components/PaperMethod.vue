<template>
  <div class="method-section">
    <h2 class="section-title">Method</h2>

    <!-- 架构图 -->
    <div class="architecture-diagram">
      <img
        src="D:\QQ\qqfile\60f08116-0af9-4de4-9b79-9db9cceaa215.png"
        alt="AST Architecture Diagram"
        class="diagram-image"
      />
    </div>

    <!-- 方法介绍 -->
    <div class="method-content">
      <p class="introduction">
        We propose an <strong>Adaptive Sparse Transformer (AST)</strong>, an efficient
        Transformer-based model for image restoration. The core goal of AST is to address two key
        issues prevalent in standard Transformer architectures: mitigating "noisy interactions from
        irrelevant regions" and removing "feature redundancy in both spatial and channel domains".
      </p>

      <p class="core-components">
        To achieve this, the AST model introduces two novel core components: an
        <strong>Adaptive Sparse Self-Attention (ASSA)</strong> block and a
        <strong>Feature Refinement Feed-forward Network (FRFN)</strong>.
      </p>

      <h3 class="subsection-title">Overall Pipeline</h3>
      <p>
        The overall architecture of AST is a symmetric encoder-decoder network, as illustrated in
        Figure 2 of the paper.
      </p>

      <div class="pipeline-steps">
        <div class="step">
          <h4>Initial Feature Extraction</h4>
          <p>
            Given a degraded image <em>I</em>, a convolution layer is first used to produce a
            low-level feature representation <em>F₀</em>.
          </p>
        </div>

        <div class="step">
          <h4>Encoder-Decoder Structure</h4>
          <p>The low-level features pass through a U-Net-like structure.</p>

          <div class="sub-components">
            <div class="component">
              <strong>Encoder:</strong> The encoder consists of multiple stages, each containing
              <em>N/2</em> basic blocks and a down-sampling convolution layer. The basic block in
              the encoder only contains an FRFN. The attention mechanism is deliberately omitted
              from the encoder because its "low-pass filter nature" can hinder the learning of
              desired local patterns, especially in the early stages of the network.
            </div>

            <div class="component">
              <strong>Bottleneck & Decoder:</strong> A bottleneck stage is introduced between the
              encoder and decoder to capture longer dependencies. The decoder then up-samples the
              features, with each stage consisting of <em>N/2</em> basic blocks that contain both an
              ASSA and an FRFN module. Skip connections fuse features from the encoder to the
              decoder.
            </div>
          </div>
        </div>

        <div class="step">
          <h4>Image Reconstruction</h4>
          <p>
            A final convolution layer produces a residual image <em>R</em> from the deep features.
            The restored image <em>Î</em> is obtained by adding the residual to the input image (<em
              >Î = I + R</em
            >). The model is trained using the Charbonnier loss.
          </p>
        </div>
      </div>

      <h3 class="subsection-title">Core Module Design</h3>

      <div class="core-modules">
        <div class="module">
          <h4>1. Adaptive Sparse Self-Attention (ASSA)</h4>
          <p>
            The ASSA module is designed to solve the trade-off between standard dense
            self-attention, which introduces noise from irrelevant regions, and simple sparse
            self-attention (e.g., ReLU-based), which can trigger information loss due to its "overly
            sparse nature".
          </p>

          <div class="module-details">
            <div class="detail">
              <strong>Dual-Branch Paradigm:</strong> ASSA consists of two branches: a sparse
              self-attention (SSA) branch and a dense self-attention (DSA) counterpart.
              <ul>
                <li>
                  The <strong>SSA branch</strong> uses "squared ReLU-based" activation to filter out
                  "features with negative impacts of low query-key matching scores".
                </li>
                <li>
                  The <strong>DSA branch</strong> employs the standard softmax layer to ensure
                  "sufficient information flow through the network for learning discriminative
                  representations".
                </li>
              </ul>
            </div>

            <div class="detail">
              <strong>Adaptive Fusion:</strong> Instead of choosing one branch over the other, ASSA
              "fuses [the] two-branch in an adaptive fashion". It uses learnable, normalized weights
              (<em>w₁, w₂</em>) to modulate the influence of the two branches, allowing the model to
              control the degree of sparsity based on the specific task.
            </div>
          </div>
        </div>

        <div class="module">
          <h4>2. Feature Refinement Feed-forward Network (FRFN)</h4>
          <p>
            The FRFN is an effective alternative to the regular feed-forward network (FFN) and is
            designed to complement ASSA by addressing channel-wise redundancy.
          </p>

          <div class="module-details">
            <div class="detail">
              <strong>Enhance-and-Ease Scheme:</strong> FRFN performs feature transformation using
              an "enhance-and-ease" scheme.
              <ul>
                <li>
                  <strong>Enhance:</strong> It incorporates a Partial Convolution (PConv) operation,
                  which acts as a sparse operation by convolving only a subset of channels, thereby
                  "reinforc[ing] the informative elements within features".
                </li>
                <li>
                  <strong>Ease:</strong> It then uses a gating mechanism to "reduce the processing
                  burden of the redundant information".
                </li>
              </ul>
            </div>
          </div>
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
