<template>
  <div class="container">
    <div class="tabs">
      <button @click="setActiveTab('1')" :class="{ active: activeName === '1' }">自述 · 平凡</button>
      <button @click="setActiveTab('2')" :class="{ active: activeName === '2' }">我的网站</button>
      <button @click="setActiveTab('3')" :class="{ active: activeName === '3' }">技能</button>
      <button @click="setActiveTab('4')" :class="{ active: activeName === '4' }">书签</button>
      <button @click="setActiveTab('5')" :class="{ active: activeName === '5' }">搜索</button>
    </div>
    <div class="tab-content">
      <div v-show="activeName == '1'" class="tab-pane">
        自述 · 平凡
      </div>
      <div v-show="activeName == '2'" class="tab-pane">
        我的网站
      </div>
      <div v-show="activeName == '3'" class="tab-pane">
        技能
      </div>
      <div v-show="activeName == '4'" class="tab-pane">
        <MyBookmarks />
      </div>
      <div v-show="activeName == '5'" class="tab-pane">
        搜索
      </div>
    </div>
  </div>
</template>
  
<script>
import MyBookmarks from '../view/my-bookmarks.vue';

export default {
  name: 'MyContent',
  components: {
    MyBookmarks
  },
  data() {
    return {
      activeName: '1'
    };
  },
  methods: {
    setActiveTab(tab) {
      this.activeName = tab;
    }
  }
};
</script>
<style scoped>
.container {
  padding: 20px;
  min-height: 920px;
  margin-top: 30px;
  width: 75%;
  border-radius: 10px;
  background: #fff;
  box-shadow: 0 4px 8px 6px rgba(7, 17, 27, .06);
  transition: all .3s;
}

.tabs {
  display: flex;
  justify-content: space-around;
  border-bottom: 1px solid #ddd;
  margin-bottom: 20px;
}

.tabs button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 16px;
  padding: 10px 20px;
  color: #333;
  transition: color 0.3s;
}

.tabs button:hover,
.tabs button.active {
  color: #007bff;
}

.tab-content {
  padding: 20px;
}
</style>