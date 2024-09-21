<!-- <template>
  <div id="app">
    <img src="./assets/cztcut1.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->

<!-- <template>
  <div class="image-container">
    <img :src="imageSrc" :alt="imageAlt" class="image" />
    <a v-for="(link, index) in links" :key="index" :href="link.url" target="_blank" class="link" :style="{ top: link.top, left: link.left }">
      {{ link.text }}
    </a>
  </div>
</template>

<script>
export default {
  data () {
    return {
      imageSrc: require('./assets/cztcut1.png'), // 图片地址
      imageAlt: '示例图片',
      links: [
        { url: 'http://localhost:8082/', text: 'NS3', top: '12%', left: '45%' },
        { url: 'https://example.com/2', text: 'HD9', top: '16%', left: '41%' },
        { url: 'https://example.com/3', text: 'HD14', top: '17%', left: '60%' }
      ]
    }
  }
}
</script>

<style scoped>
.image-container {
  position: relative;
}

.image {
  width: 100%; /* 或者设定具体宽度 */
  height: auto; /* 保持高度比例 */
}

.link {
  position: absolute;
  color: rgb(255, 255, 255); /* 链接文字颜色 */
  text-decoration: none; /* 去掉下划线 */
  background-color: rgba(0, 0, 0, 0.5); /* 背景色，增加可读性 */
  padding: 5px;
  border-radius: 5px;
}
</style> -->

<template>
  <div class="image-container">
    <img :src="imageSrc" :alt="imageAlt" class="image" />
    <button
      v-for="(button, index) in buttons"
      :key="index"
      class="button"
      :style="{ top: button.top, left: button.left }"
      @click="showImagePopup(button.imageSrc)"
    >
      {{ button.text }} <!-- 按钮文本 -->
    </button>

    <div v-if="isPopupVisible" class="popup">
      <span class="close" @click="closePopup">&times;</span>
      <img :src="popupImageSrc" alt="弹窗显示的图片" class="popup-image" />
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      imageSrc: require('./assets/cztcut2.png'),
      imageAlt: '示例图片',
      buttons: [
        { text: 'NS1', top: '29%', left: '14%', imageSrc: require('./assets/ns1.png') },
        { text: 'NS3', top: '12%', left: '45%', imageSrc: require('./assets/ns3.png') },
        { text: 'NS2', top: '20%', left: '22%', imageSrc: require('./assets/ns2.png') },
        { text: 'NS6', top: '12%', left: '77%', imageSrc: require('./assets/ns6.png') },
        { text: 'NS8', top: '28%', left: '27%', imageSrc: require('./assets/ns8.png') },
        { text: 'NS13', top: '26%', left: '49%', imageSrc: require('./assets/n13.png') },
        { text: 'LP7', top: '12%', left: '68%', imageSrc: require('./assets/lp7.png') },
        { text: 'LP8', top: '22%', left: '49%', imageSrc: require('./assets/lp8.png') },
        { text: 'HD2', top: '20%', left: '34%', imageSrc: require('./assets/hd2.png') },
        { text: 'HD4', top: '19%', left: '77%', imageSrc: require('./assets/hd4.png') }
      ],
      isPopupVisible: false, // 控制弹窗的显示状态
      popupImageSrc: '' // 存储弹窗中显示的图片 URL
    }
  },
  methods: {
    showImagePopup (src) {
      this.popupImageSrc = src // 设置弹窗中显示的图片源
      this.isPopupVisible = true // 显示弹窗
    },
    closePopup () {
      this.isPopupVisible = false // 隐藏弹窗
    }
  }
}
</script>

<style scoped>
.image-container {
  position: relative;
}
.image {
  width: 100%;
  height: auto;
}
.button {
  position: absolute;
  background-color: rgba(226, 226, 231, 0.7);
  color: white;
  border: none;
  padding: 5px;
  border-radius: 5px;
  cursor: pointer;
}
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8); /* 背景半透明阴影 */
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000; /* 确保弹窗在最上层 */
}
.popup-image {
  max-width: 80%;
  max-height: 80%; /* 图片最大宽高 */
}
.close {
  position: absolute;
  top: 20px;
  right: 30px;
  color: white;
  font-size: 30px;
  cursor: pointer; /* 鼠标悬停时显示为手形 */
}
</style>
