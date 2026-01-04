<template>
  <div style="height: 100%; display: flex; flex-direction: column;">
    <header class="page-header" style="margin-bottom: 1rem;">
      <el-button :icon="ArrowLeft" @click="router.back()">返回</el-button>
      <el-text size="large" tag="strong" style="margin-left: 1rem;">WebUI 配置</el-text>
    </header>
    <div style="flex: 1; border: 1px solid #dcdfe6; border-radius: 4px; overflow: hidden;">
      <iframe :src="url" style="width: 100%; height: 100%; border: none;"></iframe>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ArrowLeft } from '@element-plus/icons-vue';
import { useRoute, useRouter } from 'vue-router';
import { ref, onMounted } from 'vue';

const route = useRoute();
const router = useRouter();
const url = ref('');

onMounted(() => {
  const u = route.query.url as string;
  if (u) {
    url.value = u;
  }
});
</script>
