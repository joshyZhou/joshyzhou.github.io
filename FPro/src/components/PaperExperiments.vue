<template>
  <div class="experiments-section">
    <h2 class="section-title">Experiments</h2>

    <div class="experiments-content">
      <div class="quantitative-section">
        <h3 class="subsection-title">Quantitative Comparisons</h3>

        <div class="experiment-tables">
          <img
            src="/experiment-tables.png"
            alt="Quantitative comparison tables showing FPro performance across different datasets"
            class="tables-image"
          />
        </div>
      </div>

      <div class="visual-section">
        <h3 class="subsection-title">Visual Comparisons</h3>

        <div class="visual-comparisons">
          <div class="comparison-image">
            <img
              src="/visual-comparison-1.png"
              alt="Visual comparisons with state-of-the-art methods on SPAD for real rain removal"
              class="comparison-img"
            />
            <p class="image-caption">
              Visual comparisons with state-of-the-art methods on SPAD [62] for real rain removal.
            </p>
          </div>

          <div class="comparison-image">
            <img
              src="/visual-comparison-2.png"
              alt="Visual comparisons with state-of-the-art methods on AGAN-Data for raindrop removal"
              class="comparison-img"
            />
            <p class="image-caption">
              Visual comparisons with state-of-the-art methods on AGAN-Data [47] for raindrop
              removal.
            </p>
          </div>

          <div class="comparison-image">
            <img
              src="/visual-comparison-3.png"
              alt="Visual comparisons with state-of-the-art methods on TIP-2018 for moiré pattern removal"
              class="comparison-img"
            />
            <p class="image-caption">
              Visual comparisons with state-of-the-art methods on TIP-2018 [54] for moiré pattern
              removal.
            </p>
          </div>
        </div>
      </div>

      <div class="results-analysis">
        <p>
          The experimental results demonstrate the effectiveness of our FPro method across multiple
          challenging image restoration tasks. The quantitative comparisons show that FPro achieves
          competitive performance on rain streak removal (SPAD dataset), raindrop removal (AGAN-Data
          dataset), and moiré pattern removal (TIP-2018 dataset), consistently outperforming
          existing state-of-the-art methods in terms of PSNR and SSIM metrics.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.experiments-section {
  text-align: center;
}

.section-title {
  font-size: 32px;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 30px;
  text-align: center;
  font-family: 'Times New Roman', serif;
}

.experiments-content {
  margin-top: 20px;
}

.subsection-title {
  font-size: 22px;
  font-weight: 600;
  color: #2d3748;
  margin-bottom: 20px;
  text-align: center;
  font-family: 'Times New Roman', serif;
}

.experiment-tables {
  display: flex;
  justify-content: center;
  margin-bottom: 32px;
}

.tables-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.visual-section {
  margin-bottom: 32px;
}

.visual-comparisons {
  display: flex;
  flex-direction: column;
  gap: 24px;
  align-items: center;
}

.comparison-image {
  width: 100%;
  text-align: center;
}

.comparison-img {
  width: 100%;
  max-width: 800px;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  object-fit: contain;
}

.image-caption {
  font-size: 14px;
  color: #666;
  font-style: italic;
  margin-top: 10px;
  line-height: 1.4;
  text-align: center;
}

.results-analysis {
  background: #f8f9fa;
  padding: 35px;
  border-radius: 10px;
  border: 1px solid #e9ecef;
  font-size: 18px;
  text-align: justify;
  line-height: 1.8;
  color: #444;
  font-family: 'Times New Roman', serif;
  margin-top: 24px;
}

.results-analysis p {
  margin: 0;
}

.results-analysis strong {
  color: #e74c3c;
  font-weight: bold;
}
</style>
