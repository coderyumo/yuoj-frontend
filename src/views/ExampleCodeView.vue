<template>
  <div id="viewQuestionView">
    <MdViewer :value="exampleCode" />
  </div>
</template>

<script lang="ts" setup>
import MdViewer from "@/components/MdViewer.vue";

const exampleCode =
  "# 加法\n" +
  "### public class Main {\n" +
  "       public static void main(String[] args) {\n" +
  "           int a = Integer.parseInt(args[0]);\n" +
  "           int b = Integer.parseInt(args[1]);\n" +
  "           System.out.println((a + b));\n" +
  "       }\n" +
  "### }";
</script>

<style>
#viewQuestionView {
  max-width: 1400px;
  margin: 0 auto;
}

#viewQuestionView .arco-space-horizontal .arco-space-item {
  margin-bottom: 0 !important;
}
</style>
