<template>
  <div class="paper-header">
    <h1 class="title">
      Adapt or Perish: Adaptive Sparse Transformer with Attentive Feature Refinement for Image
      Restoration
    </h1>

    <div class="authors">
      <a href="https://joshyzhou.github.io/" class="author-link">Shihao Zhou<sup>1,2</sup></a
      >, <a href="https://github.com/Calvin11311" class="author-link">Duosheng Chen<sup>1</sup></a
      >, <a href="https://jspan.github.io/" class="author-link">Jinshan Pan<sup>3</sup></a
      >, <a href="https://jingleishi.github.io/" class="author-link">Jinglei Shi<sup>1*</sup></a
      >,
      <a href="https://cv.nankai.edu.cn/" class="author-link">Jufeng Yang<sup>1,2</sup></a>
    </div>

    <div class="affiliations">
      <div class="affiliation">
        <sup>1</sup> VCIP & TMCC & DISSec, College of Computer Science, Nankai University
      </div>
      <div class="affiliation">
        <sup>2</sup> Nankai International Advanced Research Institute (SHENZHEN· FUTIAN)
      </div>
      <div class="affiliation">
        <sup>3</sup> School of Computer Science and Engineering, Nanjing University of Science and
        Technology
      </div>
    </div>

    <div class="emails">
      zhoushihao96@mail.nankai.edu.cn, duoshengchen@mail.nankai.edu.cn, sdluran@gmail.com<br />
      jinglei.shi@nankai.edu.cn, yangjufeng@nankai.edu.cn
    </div>

    <div class="links">
      <a
        href="https://openaccess.thecvf.com/content/CVPR2024/html/Zhou_Adapt_or_Perish_Adaptive_Sparse_Transformer_with_Attentive_Feature_Refinement_CVPR_2024_paper.html"
        target="_blank"
        class="text-link"
        >[Paper]</a
      >
      <a
        href="https://github.com/joshyZhou/AST?tab=readme-ov-file"
        target="_blank"
        class="text-link"
        >[Github]</a
      >
      <a href="https://huggingface.co/spaces/suncongcong/AST-Demo" target="_blank" class="text-link"
        >[Huggingface]</a
      >
    </div>
  </div>
</template>

<script setup lang="ts">
// No props or reactive data needed for this static content
</script>

<style scoped>
.paper-header {
  text-align: center;
}

.title {
  font-size: 38px;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 30px;
  line-height: 1.3;
  font-family: 'Times New Roman', serif;
}

.authors {
  font-size: 22px;
  margin-bottom: 25px;
  color: #555;
  line-height: 1.6;
}

.author-link {
  color: #555;
  text-decoration: none;
  margin-right: 8px;
  transition: all 0.3s ease;
  padding: 2px 4px;
  border-radius: 4px;
  outline: none;
}

.author-link:hover {
  color: #4a90e2;
  background-color: rgba(74, 144, 226, 0.08);
}

.author-link:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(74, 144, 226, 0.2);
}

.author-link:last-child {
  margin-right: 0;
}

.affiliations {
  font-size: 16px;
  color: #666;
  margin-bottom: 15px;
  line-height: 1.5;
}

.affiliation {
  display: block;
  margin-bottom: 5px;
}

.affiliation:last-child {
  margin-bottom: 0;
}

.emails {
  font-size: 14px;
  color: #666;
  margin-bottom: 20px;
  line-height: 1.4;
  text-align: center;
}

.conference {
  font-size: 18px;
  color: #34495e;
  font-weight: 600;
  margin-bottom: 50px;
}

.links {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
  margin-top: 20px;
  padding-top: 10px;
}

.text-link {
  color: #4a90e2;
  font-size: 16px;
  font-weight: 400;
  margin: 0 15px;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  font-family: inherit;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 8px 12px;
  border-radius: 6px;
  position: relative;
  outline: none;
}

.text-link:hover {
  color: #357abd;
  background-color: rgba(74, 144, 226, 0.1);
  transform: translateY(-1px);
}

.text-link:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(74, 144, 226, 0.3);
}

sup {
  font-size: 0.8em;
  vertical-align: super;
}

@media (max-width: 768px) {
  .paper-header {
    padding: 40px 20px;
  }

  .title {
    font-size: 28px;
  }

  .authors {
    font-size: 18px;
  }

  .links {
    flex-direction: column;
    align-items: center;
  }
}
</style>
