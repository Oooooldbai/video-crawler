<template>
  <div class="container">
    <h2>视频数据采集</h2>
    <div class="input-group">
      <input 
        v-model="profileUrl" 
        placeholder="请输入视频博主主页链接"
        class="url-input"
      />
      <button 
        @click="fetchData" 
        :disabled="loading"
        class="fetch-button"
      >
        {{ loading ? '采集中...' : '开始采集' }}
      </button>
    </div>
  </div>
</template>

<script>
import { bitable } from '@base-open/web-api';

export default {
  data() {
    return {
      profileUrl: '',
      loading: false
    }
  },
  methods: {
    async fetchData() {
      if (!this.profileUrl) {
        alert('请输入视频博主主页链接');
        return;
      }
      
      this.loading = true;
      try {
        const table = await bitable.base.getActiveTable();
        // 这里添加数据采集和处理逻辑
        
        this.profileUrl = '';
        alert('数据采集完成！');
      } catch (error) {
        alert('错误：' + error.message);
      } finally {
        this.loading = false;
      }
    }
  }
}
</script>
