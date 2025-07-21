<template>
  <div class="application-section">
    <h2 class="section-title">Application</h2>

    <div class="application-content">
      <div class="demo-section">
        <h3 class="subsection-title">Interactive Image Restoration Demo</h3>

        <!-- Raindrop Removal 部分 -->
        <div class="demo-category">
          <h4 class="category-title">Raindrop Removal</h4>
          <div class="comparison-grid">
            <!-- 第一对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 1 }"
                ref="comparisonContainer1"
                @click="(e) => handleContainerClick(e, 1)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/restored-sample.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition1}% 0 0)` }"
                >
                  <img src="/original-sample.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 1 }"
                  :style="{ left: `${sliderPosition1}%` }"
                  @mousedown="(e) => startDrag(e, 1)"
                  @touchstart="(e) => startDrag(e, 1)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>

            <!-- 第二对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 2 }"
                ref="comparisonContainer2"
                @click="(e) => handleContainerClick(e, 2)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-sample-2.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition2}% 0 0)` }"
                >
                  <img src="/original-sample-2.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 2 }"
                  :style="{ left: `${sliderPosition2}%` }"
                  @mousedown="(e) => startDrag(e, 2)"
                  @touchstart="(e) => startDrag(e, 2)"
                >
                  <div class="slider-line"></div>
                </div>
              </div>
            </div>

            <!-- 第三对图片 -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 3 }"
                ref="comparisonContainer3"
                @click="(e) => handleContainerClick(e, 3)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-sample-3.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition3}% 0 0)` }"
                >
                  <img src="/original-sample-3.png" alt="Original Image" class="comparison-image" />
                </div>

                <!-- 滑动条 -->
                <div
                  class="slider-handle"
                  :class="{ locked: isSliderLocked && currentSlider === 3 }"
                  :style="{ left: `${sliderPosition3}%` }"
                  @mousedown="(e) => startDrag(e, 3)"
                  @touchstart="(e) => startDrag(e, 3)"
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

        <!-- Rainstreak Removal 部分 -->
        <div class="demo-category">
          <h4 class="category-title">Rainstreak Removal</h4>
          <div class="comparison-grid">
            <!-- 第四对图片 (rainstreak 1) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 4 }"
                ref="comparisonContainer4"
                @click="(e) => handleContainerClick(e, 4)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-rainstreak-1.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition4}% 0 0)` }"
                >
                  <img
                    src="/original-rainstreak-1.png"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

            <!-- 第五对图片 (rainstreak 2) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 5 }"
                ref="comparisonContainer5"
                @click="(e) => handleContainerClick(e, 5)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-rainstreak-2.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition5}% 0 0)` }"
                >
                  <img
                    src="/original-rainstreak-2.png"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

            <!-- 第六对图片 (rainstreak 3) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 6 }"
                ref="comparisonContainer6"
                @click="(e) => handleContainerClick(e, 6)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-rainstreak-3.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition6}% 0 0)` }"
                >
                  <img
                    src="/original-rainstreak-3.png"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

        <!-- Real Haze Removal 部分 -->
        <div class="demo-category haze-removal">
          <h4 class="category-title">Real Haze Removal</h4>
          <div class="comparison-grid">
            <!-- 第七对图片 (haze 1) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 7 }"
                ref="comparisonContainer7"
                @click="(e) => handleContainerClick(e, 7)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-haze-1-new.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition7}% 0 0)` }"
                >
                  <img
                    src="/original-haze-1-new.jpg"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

            <!-- 第八对图片 (haze 2) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 8 }"
                ref="comparisonContainer8"
                @click="(e) => handleContainerClick(e, 8)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-haze-2-new.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition8}% 0 0)` }"
                >
                  <img
                    src="/original-haze-2-new.jpg"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

            <!-- 第九对图片 (haze 3) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 9 }"
                ref="comparisonContainer9"
                @click="(e) => handleContainerClick(e, 9)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img
                    src="/restored-haze-3-new.webp"
                    alt="Restored Image"
                    class="comparison-image"
                  />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition9}% 0 0)` }"
                >
                  <img
                    src="/original-haze-3-new.jpg"
                    alt="Original Image"
                    class="comparison-image"
                  />
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

        <!-- Moiré Pattern Removal 部分 -->
        <div class="demo-category moire-removal">
          <h4 class="category-title">Moiré Pattern Removal</h4>
          <div class="comparison-grid">
            <!-- 第十对图片 (moire 1) -->
            <div class="slider-comparison">
              <div
                class="comparison-container"
                :class="{ selected: selectedComparison === 10 }"
                ref="comparisonContainer10"
                @click="(e) => handleContainerClick(e, 10)"
              >
                <!-- 修复图片 (背景，清晰的) -->
                <div class="image-layer restored-layer">
                  <img src="/restored-moire-1.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition10}% 0 0)` }"
                >
                  <img src="/original-moire-1.png" alt="Original Image" class="comparison-image" />
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
                  <img src="/restored-moire-2.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition11}% 0 0)` }"
                >
                  <img src="/original-moire-2.png" alt="Original Image" class="comparison-image" />
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
                  <img src="/restored-moire-3.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition12}% 0 0)` }"
                >
                  <img src="/original-moire-3.png" alt="Original Image" class="comparison-image" />
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

        <!-- Blur Removal 部分 -->
        <div class="demo-category blur-removal">
          <h4 class="category-title">Blur Removal</h4>
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
                  <img src="/restored-blur-1.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition13}% 0 0)` }"
                >
                  <img src="/original-blur-1.png" alt="Original Image" class="comparison-image" />
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
                  <img src="/deblur2.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition14}% 0 0)` }"
                >
                  <img src="/deblur_example2.png" alt="Original Image" class="comparison-image" />
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
                  <img src="/deblur3.webp" alt="Restored Image" class="comparison-image" />
                </div>

                <!-- 原始图片 (前景，可裁剪) -->
                <div
                  class="image-layer original-layer"
                  :style="{ clipPath: `inset(0 ${100 - sliderPosition15}% 0 0)` }"
                >
                  <img src="/deblur_example3.png" alt="Original Image" class="comparison-image" />
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

/* 统一 Moiré Pattern Removal 部分的图片大小 */
.demo-category.moire-removal .slider-comparison .comparison-container {
  height: 0;
  padding-bottom: 66.67%; /* 统一高度比例 */
}

.demo-category.moire-removal .slider-comparison .image-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.demo-category.moire-removal .slider-comparison .comparison-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

/* 统一 Blur Removal 部分的图片大小 */
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
