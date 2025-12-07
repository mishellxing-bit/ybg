<template>
  <div v-if="isOpen" class="modal-overlay" @click.self="closeModal">
    <div class="modal-container">
      <button class="modal-close" @click="closeModal" aria-label="关闭">×</button>
      
      <div class="modal-content">
        <div class="scene-info">
          <h2 class="scene-title">{{ scenes[currentScene].title }}</h2>
          <p class="scene-description">{{ scenes[currentScene].description }}</p>
        </div>
        
        <div class="video-container">
          <video 
            ref="videoPlayer"
            :src="scenes[currentScene].videoUrl" 
            controls
            autoplay
            class="demo-video"
          >
            您的浏览器不支持视频播放
          </video>
        </div>
        
        <div class="scene-navigation">
          <button 
            class="nav-arrow nav-arrow-left" 
            @click="prevScene"
            :disabled="currentScene === 0"
            aria-label="上一个场景"
          >
            ‹
          </button>
          
          <div class="scene-label">
            <span class="scene-number">{{ currentScene + 1 }} / {{ scenes.length }}</span>
            <span class="scene-name">{{ scenes[currentScene].title }}</span>
          </div>
          
          <button 
            class="nav-arrow nav-arrow-right" 
            @click="nextScene"
            :disabled="currentScene === scenes.length - 1"
            aria-label="下一个场景"
          >
            ›
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])

const currentScene = ref(0)
const videoPlayer = ref(null)

const scenes = [
  {
    title: '单表分析',
    description: '按照商品分类统计销售总额，生成柱状图',
    videoUrl: 'https://qihua-cdn.yinlintong.cn/agent_video/%E5%8D%95%E8%A1%A8%E5%88%86%E6%9E%90_%E7%94%A8%E6%88%B7%E6%84%8F%E5%9B%BE%E8%AF%86%E5%88%AB_%E5%9B%BE%E8%A1%A8%E7%94%9F%E6%88%90_%E9%A2%9C%E8%89%B2%E8%B0%83%E6%95%B4.mp4'
  },
  {
    title: '多表组合',
    description: '在\'销售员所属部门.xlsx(Sheet1)\'中增加一列所属部门，所属部门取值\'销售员所属部门.xlsx(Sheet1)\'中的\'所属部门\'，并将\'所属部门\'字段插入到\'销售员\'和\'成本价\'之间',
    videoUrl: 'https://qihua-cdn.yinlintong.cn/agent_video/%E5%A4%9A%E8%A1%A8%E7%BB%84%E5%90%88%E4%B8%BA%E6%96%B0%E8%A1%A8.mp4'
  },
  {
    title: '数据汇总',
    description: '以表格的形式展示，表头为姓名，城市及次数。规则：需要按照姓名统计城市，城市后要展示该城市的次数，多个城市之间用\'/\'分隔，如 北京 4 /上海 1',
    videoUrl: 'https://qihua-cdn.yinlintong.cn/agent_video/%E6%95%B0%E6%8D%AE%E6%B1%87%E6%80%BB%E5%8F%8A%E6%A0%BC%E5%BC%8F%E5%A4%84%E7%90%86.mp4'
  }
]

const closeModal = () => {
  emit('close')
}

const nextScene = () => {
  if (currentScene.value < scenes.length - 1) {
    currentScene.value++
  }
}

const prevScene = () => {
  if (currentScene.value > 0) {
    currentScene.value--
  }
}

const goToScene = (index) => {
  currentScene.value = index
}

// 切换场景时重新播放视频
watch(currentScene, () => {
  if (videoPlayer.value) {
    videoPlayer.value.load()
    videoPlayer.value.play()
  }
})

// 监听ESC键关闭弹窗
watch(() => props.isOpen, (isOpen) => {
  if (isOpen) {
    const handleEsc = (e) => {
      if (e.key === 'Escape') {
        closeModal()
      }
    }
    document.addEventListener('keydown', handleEsc)
    return () => document.removeEventListener('keydown', handleEsc)
  }
})
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  padding: 20px;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.modal-container {
  background: white;
  border-radius: 24px;
  max-width: 1100px;
  width: 100%;
  position: relative;
  animation: slideUp 0.4s ease;
  display: flex;
  flex-direction: column;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.modal-close {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.1);
  border: none;
  font-size: 28px;
  color: var(--text-primary);
  cursor: pointer;
  transition: all 0.3s;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 1;
}

.modal-close:hover {
  background: rgba(0, 0, 0, 0.2);
  transform: rotate(90deg);
}

.modal-content {
  padding: 48px 48px 40px;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

.scene-info {
  text-align: center;
}

.scene-title {
  font-size: 28px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 12px;
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.scene-description {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
  max-width: 800px;
  margin: 0 auto;
}

.video-container {
  background: #000;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.2);
}

.demo-video {
  width: 100%;
  height: auto;
  display: block;
  max-height: 500px;
}

.scene-navigation {
  display: flex;
  align-items: center;
  gap: 24px;
  justify-content: center;
}

.nav-arrow {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: white;
  border: 2px solid var(--border-color);
  color: var(--text-primary);
  font-size: 32px;
  font-weight: 300;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s;
  flex-shrink: 0;
}

.nav-arrow:hover:not(:disabled) {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  color: white;
  border-color: transparent;
  transform: scale(1.1);
}

.nav-arrow:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.scene-label {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  min-width: 200px;
}

.scene-number {
  font-size: 14px;
  color: var(--text-secondary);
  font-weight: 500;
}

.scene-name {
  font-size: 20px;
  font-weight: 700;
  color: var(--text-primary);
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

@media (max-width: 768px) {
  .modal-overlay {
    padding: 10px;
  }
  
  .modal-content {
    padding: 32px 20px 28px;
    gap: 20px;
  }
  
  .scene-title {
    font-size: 22px;
  }
  
  .scene-description {
    font-size: 14px;
  }
  
  .demo-video {
    max-height: 300px;
  }
  
  .scene-navigation {
    gap: 16px;
  }
  
  .scene-label {
    min-width: 140px;
  }
  
  .scene-name {
    font-size: 16px;
  }
  
  .scene-number {
    font-size: 12px;
  }
  
  .nav-arrow {
    width: 40px;
    height: 40px;
    font-size: 24px;
  }
}
</style>
