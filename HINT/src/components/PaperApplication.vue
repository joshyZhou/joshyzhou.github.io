<template>
  <div class="application-section">
    <h2 class="section-title">Application</h2>

    <div class="application-content">
      <div class="demo-section">
        <h3 class="subsection-title">Interactive Image Restoration Demo</h3>

        <!-- Raindrop Removal 部分已移除 -->

        <!-- Rainstreak Removal 部分（已替换为新图片） -->
        <div class="demo-category">
          <h4 class="category-title">Rainstreak Removal</h4>
          <div class="comparison-grid">
            <!-- 第一对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 4 }"
                ref="comparisonContainer4"
                @click="(e) => handleContainerClick(e, 4)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/derain1.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition4}% 0 0)` }"
                >
                  <img src="/derain_example1.png" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 4 }"
                  :style="{ left: `${sliderPosition4}%` }"
                  @mousedown="(e) => startDrag(e, 4)"
                  @touchstart="(e) => startDrag(e, 4)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第二对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 5 }"
                ref="comparisonContainer5"
                @click="(e) => handleContainerClick(e, 5)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/derain2.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition5}% 0 0)` }"
                >
                  <img src="/derain_example2.png" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 5 }"
                  :style="{ left: `${sliderPosition5}%` }"
                  @mousedown="(e) => startDrag(e, 5)"
                  @touchstart="(e) => startDrag(e, 5)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第三对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 6 }"
                ref="comparisonContainer6"
                @click="(e) => handleContainerClick(e, 6)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/derain3.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition6}% 0 0)` }"
                >
                  <img src="/derain_example3.png" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 6 }"
                  :style="{ left: `${sliderPosition6}%` }"
                  @mousedown="(e) => startDrag(e, 6)"
                  @touchstart="(e) => startDrag(e, 6)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>

        <!-- Real Haze Removal 部分（已替换为新图片） -->
        <div class="demo-category haze-removal">
          <h4 class="category-title">Real Haze Removal</h4>
          <div class="comparison-grid">
            <!-- 第一对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 7 }"
                ref="comparisonContainer7"
                @click="(e) => handleContainerClick(e, 7)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/dehaze1.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition7}% 0 0)` }"
                >
                  <img src="/dahaze_example1.jpg" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 7 }"
                  :style="{ left: `${sliderPosition7}%` }"
                  @mousedown="(e) => startDrag(e, 7)"
                  @touchstart="(e) => startDrag(e, 7)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第二对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 8 }"
                ref="comparisonContainer8"
                @click="(e) => handleContainerClick(e, 8)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/dehaze2.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition8}% 0 0)` }"
                >
                  <img src="/dehaze_example2.jpg" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 8 }"
                  :style="{ left: `${sliderPosition8}%` }"
                  @mousedown="(e) => startDrag(e, 8)"
                  @touchstart="(e) => startDrag(e, 8)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第三对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 9 }"
                ref="comparisonContainer9"
                @click="(e) => handleContainerClick(e, 9)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/dehaze3.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition9}% 0 0)` }"
                >
                  <img src="/dehaze_example3.jpg" alt="Original Image" class="comparison-image" />
                </div>
                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 9 }"
                  :style="{ left: `${sliderPosition9}%` }"
                  @mousedown="(e) => startDrag(e, 9)"
                  @touchstart="(e) => startDrag(e, 9)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>

        <!-- Noise Removal 部分 -->
        <div class="demo-category noise-removal">
          <h4 class="category-title">Noise Removal</h4>
          <div class="comparison-grid">
            <!-- 第十对图片 (noise 1) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 10 }"
                ref="comparisonContainer10"
                @click="(e) => handleContainerClick(e, 10)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/denose2.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition10}% 0 0)` }"
                >
                  <img src="/denose_example2.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 10 }"
                  :style="{ left: `${sliderPosition10}%` }"
                  @mousedown="(e) => startDrag(e, 10)"
                  @touchstart="(e) => startDrag(e, 10)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
              Noise Removal
            </div>

            <!-- 第十一对图片 (moire 2) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 11 }"
                ref="comparisonContainer11"
                @click="(e) => handleContainerClick(e, 11)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/denose1.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition11}% 0 0)` }"
                >
                  <img src="/denose_example1.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 11 }"
                  :style="{ left: `${sliderPosition11}%` }"
                  @mousedown="(e) => startDrag(e, 11)"
                  @touchstart="(e) => startDrag(e, 11)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>

            <!-- 第十二对图片 (moire 3) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 12 }"
                ref="comparisonContainer12"
                @click="(e) => handleContainerClick(e, 12)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/sample20.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition12}% 0 0)` }"
                >
                  <img src="/sample_20.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 12 }"
                  :style="{ left: `${sliderPosition12}%` }"
                  @mousedown="(e) => startDrag(e, 12)"
                  @touchstart="(e) => startDrag(e, 12)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>

          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>

        <!-- Snow Removal 部分 -->
        <div class="demo-category blur-removal">
          <h4 class="category-title">Snow Removal</h4>
          <div class="comparison-grid">
            <!-- 第十三对图片 (blur 1) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 13 }"
                ref="comparisonContainer13"
                @click="(e) => handleContainerClick(e, 13)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/desnow1.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition13}% 0 0)` }"
                >
                  <img src="/desnow_example1.jpg" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 13 }"
                  :style="{ left: `${sliderPosition13}%` }"
                  @mousedown="(e) => startDrag(e, 13)"
                  @touchstart="(e) => startDrag(e, 13)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>

            <!-- 第十四对图片 (blur 2) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 14 }"
                ref="comparisonContainer14"
                @click="(e) => handleContainerClick(e, 14)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/desnow2.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition14}% 0 0)` }"
                >
                  <img src="/desnow_example2.jpg" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 14 }"
                  :style="{ left: `${sliderPosition14}%` }"
                  @mousedown="(e) => startDrag(e, 14)"
                  @touchstart="(e) => startDrag(e, 14)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>

            <!-- 第十五对图片 (blur 3) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 15 }"
                ref="comparisonContainer15"
                @click="(e) => handleContainerClick(e, 15)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/desnow3.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition15}% 0 0)` }"
                >
                  <img src="/desnow_example3.jpg" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 15 }"
                  :style="{ left: `${sliderPosition15}%` }"
                  @mousedown="(e) => startDrag(e, 15)"
                  @touchstart="(e) => startDrag(e, 15)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>

          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>

        <!-- Low-Light Enhancement-syn 部分 -->
        <div class="demo-category syn-enhancement">
          <h4 class="category-title">Low-Light Enhancement-syn</h4>
          <div class="comparison-grid">
            <!-- 第一对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 16 }"
                ref="comparisonContainer16"
                @click="(e) => handleContainerClick(e, 16)"
              >
                <div class="image-layer restored-layer">
                  <img src="/syn1.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition16}% 0 0)` }"
                >
                  <img src="/syn_example1.png" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 16 }"
                  :style="{ left: `${sliderPosition16}%` }"
                  @mousedown="(e) => startDrag(e, 16)"
                  @touchstart="(e) => startDrag(e, 16)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第二对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 17 }"
                ref="comparisonContainer17"
                @click="(e) => handleContainerClick(e, 17)"
              >
                <div class="image-layer restored-layer">
                  <img src="/syn2.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition17}% 0 0)` }"
                >
                  <img src="/syn_example2.png" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 17 }"
                  :style="{ left: `${sliderPosition17}%` }"
                  @mousedown="(e) => startDrag(e, 17)"
                  @touchstart="(e) => startDrag(e, 17)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第三对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 18 }"
                ref="comparisonContainer18"
                @click="(e) => handleContainerClick(e, 18)"
              >
                <div class="image-layer restored-layer">
                  <img src="/syn3.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition18}% 0 0)` }"
                >
                  <img src="/syn_example3.png" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 18 }"
                  :style="{ left: `${sliderPosition18}%` }"
                  @mousedown="(e) => startDrag(e, 18)"
                  @touchstart="(e) => startDrag(e, 18)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>

        <!-- Low-Light Enhancement-real 部分 -->
        <div class="demo-category real-enhancement">
          <h4 class="category-title">Low-Light Enhancement-real</h4>
          <div class="comparison-grid">
            <!-- 第一对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 19 }"
                ref="comparisonContainer19"
                @click="(e) => handleContainerClick(e, 19)"
              >
                <div class="image-layer restored-layer">
                  <img src="/real1.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition19}% 0 0)` }"
                >
                  <img src="/real_example1.png" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 19 }"
                  :style="{ left: `${sliderPosition19}%` }"
                  @mousedown="(e) => startDrag(e, 19)"
                  @touchstart="(e) => startDrag(e, 19)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第二对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 20 }"
                ref="comparisonContainer20"
                @click="(e) => handleContainerClick(e, 20)"
              >
                <div class="image-layer restored-layer">
                  <img src="/real2.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition20}% 0 0)` }"
                >
                  <img src="/real_example2.jpg" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 20 }"
                  :style="{ left: `${sliderPosition20}%` }"
                  @mousedown="(e) => startDrag(e, 20)"
                  @touchstart="(e) => startDrag(e, 20)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
            <!-- 第三对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 21 }"
                ref="comparisonContainer21"
                @click="(e) => handleContainerClick(e, 21)"
              >
                <div class="image-layer restored-layer">
                  <img src="/real3.webp" alt="Restored Image" class="comparison-image" />
                </div>
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition21}% 0 0)` }"
                >
                  <img src="/real_example3.png" alt="Original Image" class="comparison-image" />
                </div>
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 21 }"
                  :style="{ left: `${sliderPosition21}%` }"
                  @mousedown="(e) => startDrag(e, 21)"
                  @touchstart="(e) => startDrag(e, 21)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="instructions">
            <p>
              Drag the slider to compare images: slide left to view restoration results, slide right
              to view original images
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onUnmounted } from 'vue'

const sliderPosition1 = ref(50) // 第一对图片滑动条位置
const sliderPosition2 = ref(50) // 第二对图片滑动条位置
const sliderPosition3 = ref(50) // 第三对图片滑动条位置
const sliderPosition4 = ref(50) // 第四对图片滑动条位置 (rainstreak 1)
const sliderPosition5 = ref(50) // 第五对图片滑动条位置 (rainstreak 2)
const sliderPosition6 = ref(50) // 第六对图片滑动条位置 (rainstreak 3)
const sliderPosition7 = ref(50) // 第七对图片滑动条位置 (haze 1)
const sliderPosition8 = ref(50) // 第八对图片滑动条位置 (haze 2)
const sliderPosition9 = ref(50) // 第九对图片滑动条位置 (haze 3)
const sliderPosition10 = ref(50) // 第十对图片滑动条位置 (moire 1)
const sliderPosition11 = ref(50) // 第十一对图片滑动条位置 (moire 2)
const sliderPosition12 = ref(50) // 第十二对图片滑动条位置 (moire 3)
const sliderPosition13 = ref(50) // 第十三对图片滑动条位置 (blur 1)
const sliderPosition14 = ref(50) // 第十四对图片滑动条位置 (blur 2)
const sliderPosition15 = ref(50) // 第十五对图片滑动条位置 (blur 3)
const sliderPosition16 = ref(50) // 第十六对图片滑动条位置 (syn 1)
const sliderPosition17 = ref(50) // 第十七对图片滑动条位置 (syn 2)
const sliderPosition18 = ref(50) // 第十八对图片滑动条位置 (syn 3)
const sliderPosition19 = ref(50) // 第十九对图片滑动条位置 (real 1)
const sliderPosition20 = ref(50) // 第二十对图片滑动条位置 (real 2)
const sliderPosition21 = ref(50) // 第二十一对图片滑动条位置 (real 3)
const selectedComparison = ref(0) // 当前选中的图片对比组件
const comparisonContainer1 = ref<HTMLElement | null>(null)
const comparisonContainer2 = ref<HTMLElement | null>(null)
const comparisonContainer3 = ref<HTMLElement | null>(null)
const comparisonContainer4 = ref<HTMLElement | null>(null)
const comparisonContainer5 = ref<HTMLElement | null>(null)
const comparisonContainer6 = ref<HTMLElement | null>(null)
const comparisonContainer7 = ref<HTMLElement | null>(null)
const comparisonContainer8 = ref<HTMLElement | null>(null)
const comparisonContainer9 = ref<HTMLElement | null>(null)
const comparisonContainer10 = ref<HTMLElement | null>(null)
const comparisonContainer11 = ref<HTMLElement | null>(null)
const comparisonContainer12 = ref<HTMLElement | null>(null)
const comparisonContainer13 = ref<HTMLElement | null>(null)
const comparisonContainer14 = ref<HTMLElement | null>(null)
const comparisonContainer15 = ref<HTMLElement | null>(null)
const comparisonContainer16 = ref<HTMLElement | null>(null)
const comparisonContainer17 = ref<HTMLElement | null>(null)
const comparisonContainer18 = ref<HTMLElement | null>(null)
const comparisonContainer19 = ref<HTMLElement | null>(null)
const comparisonContainer20 = ref<HTMLElement | null>(null)
const comparisonContainer21 = ref<HTMLElement | null>(null)
const isDragging = ref(false)
const isSliderLocked = ref(false) // 滑动条是否被锁定（点击锁定模式）
const currentSlider = ref(0) // 当前拖拽的滑动条

// 处理容器点击事件，平滑滑动到点击位置
const handleContainerClick = (event: MouseEvent, sliderIndex: number) => {
  // 如果正在拖拽，不处理点击事件
  if (isDragging.value) return

  // 设置选中状态
  selectedComparison.value = sliderIndex

  let container: HTMLElement | null = null
  let position: typeof sliderPosition1 = sliderPosition1

  // 根据滑动条索引选择对应的容器和位置变量
  switch (sliderIndex) {
    case 1:
      container = comparisonContainer1.value
      position = sliderPosition1
      break
    case 2:
      container = comparisonContainer2.value
      position = sliderPosition2
      break
    case 3:
      container = comparisonContainer3.value
      position = sliderPosition3
      break
    case 4:
      container = comparisonContainer4.value
      position = sliderPosition4
      break
    case 5:
      container = comparisonContainer5.value
      position = sliderPosition5
      break
    case 6:
      container = comparisonContainer6.value
      position = sliderPosition6
      break
    case 7:
      container = comparisonContainer7.value
      position = sliderPosition7
      break
    case 8:
      container = comparisonContainer8.value
      position = sliderPosition8
      break
    case 9:
      container = comparisonContainer9.value
      position = sliderPosition9
      break
    case 10:
      container = comparisonContainer10.value
      position = sliderPosition10
      break
    case 11:
      container = comparisonContainer11.value
      position = sliderPosition11
      break
    case 12:
      container = comparisonContainer12.value
      position = sliderPosition12
      break
    case 13:
      container = comparisonContainer13.value
      position = sliderPosition13
      break
    case 14:
      container = comparisonContainer14.value
      position = sliderPosition14
      break
    case 15:
      container = comparisonContainer15.value
      position = sliderPosition15
      break
    case 16:
      container = comparisonContainer16.value
      position = sliderPosition16
      break
    case 17:
      container = comparisonContainer17.value
      position = sliderPosition17
      break
    case 18:
      container = comparisonContainer18.value
      position = sliderPosition18
      break
    case 19:
      container = comparisonContainer19.value
      position = sliderPosition19
      break
    case 20:
      container = comparisonContainer20.value
      position = sliderPosition20
      break
    case 21:
      container = comparisonContainer21.value
      position = sliderPosition21
      break
  }

  if (!container) return

  const rect = container.getBoundingClientRect()
  const x = event.clientX - rect.left
  const targetPercentage = Math.max(0, Math.min(100, (x / rect.width) * 100))

  // 使用动画平滑移动到目标位置
  animateSlider(position, targetPercentage)
}

// 平滑动画函数
const animateSlider = (position: typeof sliderPosition1, targetValue: number) => {
  const startValue = position.value
  const difference = targetValue - startValue
  const duration = 300 // 300ms 动画时长
  const startTime = performance.now()

  const animate = (currentTime: number) => {
    const elapsed = currentTime - startTime
    const progress = Math.min(elapsed / duration, 1)

    // 使用 easeOutCubic 缓动函数
    const easeOutCubic = (t: number) => 1 - Math.pow(1 - t, 3)
    const easedProgress = easeOutCubic(progress)

    position.value = startValue + difference * easedProgress

    if (progress < 1) {
      requestAnimationFrame(animate)
    }
  }

  requestAnimationFrame(animate)
}

// 开始拖拽
const startDrag = (event: MouseEvent | TouchEvent, sliderIndex: number) => {
  // 检查是否点击了滑动条手柄
  const target = event.target as HTMLElement
  const isSliderHandle = target.closest('.slider-handle')

  if (isSliderHandle) {
    // 点击滑动条时切换锁定状态
    if (isSliderLocked.value && currentSlider.value === sliderIndex) {
      // 如果当前滑动条已锁定，解锁它
      unlockSlider()
      return
    } else {
      // 锁定当前滑动条
      lockSlider(sliderIndex)
      return
    }
  }

  // 正常的拖拽逻辑
  isDragging.value = true
  currentSlider.value = sliderIndex
  event.preventDefault()

  // 拖拽时禁用过渡效果
  disableTransitions(sliderIndex)

  // 添加全局事件监听器
  if (event instanceof MouseEvent) {
    document.addEventListener('mousemove', onDrag)
    document.addEventListener('mouseup', stopDrag)
  } else {
    document.addEventListener('touchmove', onDrag)
    document.addEventListener('touchend', stopDrag)
  }
}

// 拖拽过程中
const onDrag = (event: MouseEvent | TouchEvent) => {
  if (!isDragging.value && !isSliderLocked.value) return

  let container: HTMLElement | null = null
  let position: typeof sliderPosition1 = sliderPosition1

  // 根据当前滑动条选择对应的容器和位置变量
  switch (currentSlider.value) {
    case 1:
      container = comparisonContainer1.value
      position = sliderPosition1
      break
    case 2:
      container = comparisonContainer2.value
      position = sliderPosition2
      break
    case 3:
      container = comparisonContainer3.value
      position = sliderPosition3
      break
    case 4:
      container = comparisonContainer4.value
      position = sliderPosition4
      break
    case 5:
      container = comparisonContainer5.value
      position = sliderPosition5
      break
    case 6:
      container = comparisonContainer6.value
      position = sliderPosition6
      break
    case 7:
      container = comparisonContainer7.value
      position = sliderPosition7
      break
    case 8:
      container = comparisonContainer8.value
      position = sliderPosition8
      break
    case 9:
      container = comparisonContainer9.value
      position = sliderPosition9
      break
    case 10:
      container = comparisonContainer10.value
      position = sliderPosition10
      break
    case 11:
      container = comparisonContainer11.value
      position = sliderPosition11
      break
    case 12:
      container = comparisonContainer12.value
      position = sliderPosition12
      break
    case 13:
      container = comparisonContainer13.value
      position = sliderPosition13
      break
    case 14:
      container = comparisonContainer14.value
      position = sliderPosition14
      break
    case 15:
      container = comparisonContainer15.value
      position = sliderPosition15
      break
    case 16:
      container = comparisonContainer16.value
      position = sliderPosition16
      break
    case 17:
      container = comparisonContainer17.value
      position = sliderPosition17
      break
    case 18:
      container = comparisonContainer18.value
      position = sliderPosition18
      break
    case 19:
      container = comparisonContainer19.value
      position = sliderPosition19
      break
    case 20:
      container = comparisonContainer20.value
      position = sliderPosition20
      break
    case 21:
      container = comparisonContainer21.value
      position = sliderPosition21
      break
  }

  if (!container) return

  const rect = container.getBoundingClientRect()
  let clientX: number

  if (event instanceof MouseEvent) {
    clientX = event.clientX
  } else {
    clientX = event.touches[0].clientX
  }

  const x = clientX - rect.left
  const percentage = Math.max(0, Math.min(100, (x / rect.width) * 100))
  position.value = percentage
}

// 锁定滑动条（点击锁定模式）
const lockSlider = (sliderIndex: number) => {
  isSliderLocked.value = true
  currentSlider.value = sliderIndex

  // 禁用过渡效果
  disableTransitions(sliderIndex)

  // 添加鼠标移动监听器
  document.addEventListener('mousemove', onDrag)
  document.addEventListener('click', unlockSlider)
}

// 解锁滑动条
const unlockSlider = () => {
  const prevSlider = currentSlider.value
  isSliderLocked.value = false

  // 重新启用过渡效果
  enableTransitions(prevSlider)

  // 移除监听器
  document.removeEventListener('mousemove', onDrag)
  document.removeEventListener('click', unlockSlider)
}

// 停止拖拽
const stopDrag = () => {
  const prevSlider = currentSlider.value
  isDragging.value = false
  currentSlider.value = 0

  // 拖拽结束后重新启用过渡效果
  enableTransitions(prevSlider)

  document.removeEventListener('mousemove', onDrag)
  document.removeEventListener('mouseup', stopDrag)
  document.removeEventListener('touchmove', onDrag)
  document.removeEventListener('touchend', stopDrag)
}

// 禁用过渡效果
const disableTransitions = (sliderIndex: number) => {
  let container: HTMLElement | null = null

  switch (sliderIndex) {
    case 1:
      container = comparisonContainer1.value
      break
    case 2:
      container = comparisonContainer2.value
      break
    case 3:
      container = comparisonContainer3.value
      break
    case 4:
      container = comparisonContainer4.value
      break
    case 5:
      container = comparisonContainer5.value
      break
    case 6:
      container = comparisonContainer6.value
      break
    case 7:
      container = comparisonContainer7.value
      break
    case 8:
      container = comparisonContainer8.value
      break
    case 9:
      container = comparisonContainer9.value
      break
    case 10:
      container = comparisonContainer10.value
      break
    case 11:
      container = comparisonContainer11.value
      break
    case 12:
      container = comparisonContainer12.value
      break
    case 13:
      container = comparisonContainer13.value
      break
    case 14:
      container = comparisonContainer14.value
      break
    case 15:
      container = comparisonContainer15.value
      break
    case 16:
      container = comparisonContainer16.value
      break
    case 17:
      container = comparisonContainer17.value
      break
    case 18:
      container = comparisonContainer18.value
      break
    case 19:
      container = comparisonContainer19.value
      break
    case 20:
      container = comparisonContainer20.value
      break
    case 21:
      container = comparisonContainer21.value
      break
  }

  if (container) {
    const handle = container.querySelector('.slider-handle') as HTMLElement
    const originalLayer = container.querySelector('.original-layer') as HTMLElement

    if (handle) handle.style.transition = 'none'
    if (originalLayer) originalLayer.style.transition = 'none'
  }
}

// 启用过渡效果
const enableTransitions = (sliderIndex: number) => {
  let container: HTMLElement | null = null

  switch (sliderIndex) {
    case 1:
      container = comparisonContainer1.value
      break
    case 2:
      container = comparisonContainer2.value
      break
    case 3:
      container = comparisonContainer3.value
      break
    case 4:
      container = comparisonContainer4.value
      break
    case 5:
      container = comparisonContainer5.value
      break
    case 6:
      container = comparisonContainer6.value
      break
    case 7:
      container = comparisonContainer7.value
      break
    case 8:
      container = comparisonContainer8.value
      break
    case 9:
      container = comparisonContainer9.value
      break
    case 10:
      container = comparisonContainer10.value
      break
    case 11:
      container = comparisonContainer11.value
      break
    case 12:
      container = comparisonContainer12.value
      break
    case 13:
      container = comparisonContainer13.value
      break
    case 14:
      container = comparisonContainer14.value
      break
    case 15:
      container = comparisonContainer15.value
      break
    case 16:
      container = comparisonContainer16.value
      break
    case 17:
      container = comparisonContainer17.value
      break
    case 18:
      container = comparisonContainer18.value
      break
    case 19:
      container = comparisonContainer19.value
      break
    case 20:
      container = comparisonContainer20.value
      break
    case 21:
      container = comparisonContainer21.value
      break
  }

  if (container) {
    const handle = container.querySelector('.slider-handle') as HTMLElement
    const originalLayer = container.querySelector('.original-layer') as HTMLElement

    if (handle) handle.style.transition = 'left 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94)'
    if (originalLayer)
      originalLayer.style.transition = 'clip-path 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94)'
  }
}

// 清理事件监听器
onUnmounted(() => {
  document.removeEventListener('mousemove', onDrag)
  document.removeEventListener('mouseup', stopDrag)
  document.removeEventListener('touchmove', onDrag)
  document.removeEventListener('touchend', stopDrag)
  document.removeEventListener('click', unlockSlider)
})
</script>

<style scoped>
/* .application-section 样式由 App.vue 中的全局样式控制 */

.section-title {
  font-size: 32px;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 30px;
  text-align: center;
  font-family: 'Times New Roman', serif;
}

.subsection-title {
  font-size: 24px;
  font-weight: bold;
  color: #34495e;
  margin: 35px 0 20px 0;
  padding-bottom: 8px;
  text-align: center;
}

.demo-section {
  margin-bottom: 40px;
}

.demo-category {
  margin-bottom: 50px;
}

.category-title {
  font-size: 20px;
  font-weight: bold;
  color: #2c3e50;
  margin: 25px 0 20px 0;
  text-align: center;
  border-bottom: 2px solid #3498db;
  padding-bottom: 8px;
}

.comparison-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin: 30px 0;
}

/* 滑动对比器样式 */
.slider-comparison {
  margin: 0;
}

.comparison-container {
  position: relative;
  width: 100%;
  max-width: 100%;
  margin: 0 auto;
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
  cursor: ew-resize;
  transition:
    border 0.3s ease,
    box-shadow 0.3s ease;
  border: 3px solid transparent;
}

.comparison-container.selected {
  box-shadow:
    0 8px 24px rgba(0, 0, 0, 0.15),
    0 0 0 0.01px rgba(255, 255, 255, 1),
    0 0 0 2px rgba(0, 0, 0, 1);
}

.image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.original-layer {
  z-index: 1;
  transition: clip-path 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.restored-layer {
  position: relative;
}

.comparison-image {
  width: 100%;
  height: auto;
  display: block;
  user-select: none;
  pointer-events: none;
}

/* 限制第一对图片的高度以匹配其他图片 */
.demo-category:first-child .slider-comparison:first-child .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 1920/1280 = 1.5, 所以 1/1.5 = 0.6667 = 66.67% */
}

.demo-category:first-child .slider-comparison:first-child .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category:first-child .slider-comparison:first-child .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Real Haze Removal 部分的图片大小 */
.demo-category.haze-removal .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.haze-removal .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.haze-removal .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Noise Removal 部分的图片大小 */
.demo-category.noise-removal .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.noise-removal .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.noise-removal .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Snow Removal 部分的图片大小 */
.demo-category.blur-removal .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.blur-removal .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.blur-removal .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Low-Light Enhancement-syn 部分的图片大小 */
.demo-category.syn-enhancement .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.syn-enhancement .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.syn-enhancement .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Low-Light Enhancement-real 部分的图片大小 */
.demo-category.real-enhancement .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.real-enhancement .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.real-enhancement .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

.image-label {
  position: absolute;
  top: 20px;
  padding: 8px 16px;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  border-radius: 6px;
  font-size: 14px;
  font-weight: bold;
  z-index: 2;
  display: none; /* 隐藏文字标签 */
}

.original-label {
  left: 20px;
}

.restored-label {
  right: 20px;
}

/* 滑动条样式 */
.slider-handle {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 6px;
  background: transparent;
  cursor: ew-resize;
  z-index: 3;
  transform: translateX(-50%);
  transition: left 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.slider-handle:hover .slider-line {
  background: rgba(255, 255, 255, 0.8);
  width: 2px;
}

.slider-line {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 1px;
  background: rgba(255, 255, 255, 0.4);
  transform: translateX(-50%);
  transition: all 0.2s ease;
}

/* 锁定状态的滑动条样式 */
.slider-handle.locked .slider-line {
  background: rgba(255, 255, 255, 0.6);
  width: 3px;
  box-shadow: 0 0 8px rgba(255, 255, 255, 0.3);
}

.instructions {
  text-align: center;
  margin: 20px 0;
  color: #666;
  font-style: italic;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .application-section {
    padding: 20px;
  }

  .comparison-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .comparison-container {
    max-width: 100%;
  }

  .slider-circle {
    width: 40px;
    height: 40px;
  }

  .image-label {
    font-size: 12px;
    padding: 6px 12px;
  }

  .original-label {
    left: 10px;
    top: 10px;
  }

  .restored-label {
    right: 10px;
    top: 10px;
  }
}

@media (max-width: 1024px) {
  .comparison-grid {
    grid-template-columns: 1fr;
    gap: 25px;
  }
}

/* 防止图片被选中 */
.comparison-container * {
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
}
</style>
