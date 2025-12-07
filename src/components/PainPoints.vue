<template>
  <section id="users" class="pain-points">
    <div class="container">
      <div class="carousel-container">
        <div class="carousel-content">
          <transition :name="transitionName" mode="out-in">
            <div v-if="currentSlide === 0" key="pain" class="tab-panel">
              <div class="section-header">
                <h2 class="section-title">是否正在为这些问题而烦恼？</h2>
                <p class="section-subtitle">我们理解您的痛点，易表格为您提供完美解决方案</p>
              </div>
              <div class="pain-grid">
                <div class="pain-card">
                  <div class="pain-icon">😫</div>
                  <h3 class="pain-title">复杂的表格处理</h3>
                  <p class="pain-desc">是否因为处理复杂的表格而觉得头疼不已？</p>
                </div>
                <div class="pain-card">
                  <div class="pain-icon">🤯</div>
                  <h3 class="pain-title">繁琐的公式编写</h3>
                  <p class="pain-desc">是否在为编写各种公式处理数据而感到繁琐？</p>
                </div>
                <div class="pain-card">
                  <div class="pain-icon">⏰</div>
                  <h3 class="pain-title">耗时的图表制作</h3>
                  <p class="pain-desc">制作数据图表耗时费力，效率低下？</p>
                </div>
              </div>
            </div>
            
            <div v-else-if="currentSlide === 1" key="users" class="tab-panel">
              <div class="section-header">
                <h2 class="section-title">为谁而设计？</h2>
                <p class="section-subtitle">专为需要高效处理Excel但不想学习复杂公式的人群打造</p>
              </div>
              <div class="users-grid">
                <div v-for="user in users" :key="user.id" class="user-card">
                  <div class="user-icon">{{ user.icon }}</div>
                  <div class="user-info">
                    <h3 class="user-title">{{ user.title }}</h3>
                    <p class="user-desc">{{ user.description }}</p>
                  </div>
                </div>
              </div>
            </div>
            
            <div v-else key="pursuit" class="tab-panel">
              <div class="section-header">
                <h2 class="section-title">他们追求什么？</h2>
                <p class="section-subtitle">让数据分析变得简单高效，满足不同场景的需求</p>
              </div>
              <div class="pursuit-section-full">
                <div class="pursuit-items-large">
                  <div class="pursuit-item-large">
                    <span class="pursuit-icon-large">⚡</span>
                    <h3 class="pursuit-text-large">效率至上</h3>
                    <p class="pursuit-desc">快速完成数据处理，节省宝贵时间</p>
                  </div>
                  <div class="pursuit-item-large">
                    <span class="pursuit-icon-large">✨</span>
                    <h3 class="pursuit-text-large">简洁易用</h3>
                    <p class="pursuit-desc">无需学习复杂公式，上手即用</p>
                  </div>
                  <div class="pursuit-item-large">
                    <span class="pursuit-icon-large">📊</span>
                    <h3 class="pursuit-text-large">快速洞察</h3>
                    <p class="pursuit-desc">一键生成数据可视化图表</p>
                  </div>
                  <div class="pursuit-item-large">
                    <span class="pursuit-icon-large">🎯</span>
                    <h3 class="pursuit-text-large">精准分析</h3>
                    <p class="pursuit-desc">智能计算保证结果准确可靠</p>
                  </div>
                </div>
              </div>
            </div>
          </transition>
        </div>
        
        <div class="carousel-dots">
          <button 
            v-for="(slide, index) in 3" 
            :key="index"
            :class="['dot', { active: currentSlide === index }]"
            @click="goToSlide(index)"
            :aria-label="`切换到第${index + 1}页`"
          ></button>
        </div>
      </div>
      
      <div class="solution-banner">
        <div class="solution-content">
          <div class="solution-icon">✨</div>
          <div class="solution-text">
            <h3>易表格：一句话搞定复杂计算</h3>
            <p>智能处理Excel数据，让数据分析变得简单高效</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
const transitionName = ref('slide-right')
let autoPlayInterval = null

const goToSlide = (index) => {
  transitionName.value = index > currentSlide.value ? 'slide-left' : 'slide-right'
  currentSlide.value = index
  resetAutoPlay()
}

const nextSlide = () => {
  transitionName.value = 'slide-left'
  currentSlide.value = (currentSlide.value + 1) % 3
}

const prevSlide = () => {
  transitionName.value = 'slide-right'
  currentSlide.value = currentSlide.value === 0 ? 2 : currentSlide.value - 1
  resetAutoPlay()
}

const startAutoPlay = () => {
  autoPlayInterval = setInterval(nextSlide, 5000)
}

const resetAutoPlay = () => {
  if (autoPlayInterval) {
    clearInterval(autoPlayInterval)
  }
  startAutoPlay()
}

onMounted(() => {
  startAutoPlay()
  
  // 监听从 Header 触发的切换事件
  window.addEventListener('switchToUsers', () => {
    goToSlide(1) // 切换到第2页（为谁而设计）
  })
})

onUnmounted(() => {
  if (autoPlayInterval) {
    clearInterval(autoPlayInterval)
  }
  window.removeEventListener('switchToUsers', () => {})
})

const users = [
  {
    id: 1,
    icon: '💼',
    title: '职场人士',
    description: '市场、运营、销售、行政、HR等经常与Excel打交道但并非数据专家的职场人士'
  },
  {
    id: 2,
    icon: '🎓',
    title: '学生群体',
    description: '需要处理数据作业、统计分析但不熟悉复杂Excel功能的在校学生'
  },
  {
    id: 3,
    icon: '👨‍🏫',
    title: '教师群体',
    description: '需要快速处理成绩统计、数据分析的教师，追求高效便捷的工具'
  },
  {
    id: 4,
    icon: '🏢',
    title: '小企业主',
    description: '需要处理财务报表、销售数据但没有专业数据团队的小企业经营者'
  }
]

defineExpose({
  goToSlide
})
</script>

<style scoped>
.pain-points {
  padding: 80px 0 60px;
  background: linear-gradient(180deg, #FAFAFA 0%, #FFFFFF 100%);
}

.carousel-container {
  margin-bottom: 48px;
  position: relative;
}

.carousel-content {
  position: relative;
  min-height: 500px;
  overflow: hidden;
}

.tab-panel {
  width: 100%;
}

.slide-left-enter-active,
.slide-left-leave-active,
.slide-right-enter-active,
.slide-right-leave-active {
  transition: all 0.5s ease;
}

.slide-left-enter-from {
  opacity: 0;
  transform: translateX(100%);
}

.slide-left-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}

.slide-right-enter-from {
  opacity: 0;
  transform: translateX(-100%);
}

.slide-right-leave-to {
  opacity: 0;
  transform: translateX(100%);
}

.carousel-dots {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 40px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #D1D5DB;
  border: none;
  padding: 0;
  cursor: pointer;
  transition: all 0.3s;
}

.dot:hover {
  background: #9CA3AF;
  transform: scale(1.2);
}

.dot.active {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  width: 32px;
  border-radius: 6px;
}

.section-header {
  text-align: center;
  margin-bottom: 48px;
}

.section-title {
  font-size: 40px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 16px;
}

.section-subtitle {
  font-size: 18px;
  color: var(--text-secondary);
}

.pain-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.pain-card {
  background: white;
  padding: 32px;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  transition: all 0.3s;
  text-align: center;
}

.pain-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.12);
}

.pain-icon {
  font-size: 56px;
  margin-bottom: 20px;
}

.pain-title {
  font-size: 20px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 12px;
}

.pain-desc {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
}

.users-content {
  display: flex;
  flex-direction: column;
  gap: 48px;
}

.users-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}

.pursuit-section-full {
  width: 100%;
}

.pursuit-items-large {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
}

.pursuit-item-large {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 16px;
  padding: 40px 32px;
  background: white;
  border-radius: 20px;
  transition: all 0.4s;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.pursuit-item-large:hover {
  transform: translateY(-12px);
  box-shadow: 0 12px 40px rgba(0, 196, 140, 0.25);
}

.pursuit-icon-large {
  font-size: 64px;
}

.pursuit-text-large {
  font-size: 22px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 8px;
}

.pursuit-desc {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
}

.user-card {
  background: white;
  padding: 32px;
  border-radius: 16px;
  display: flex;
  align-items: center;
  gap: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  transition: all 0.3s;
  min-height: 140px;
}

.user-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
}

.user-icon {
  font-size: 56px;
  flex-shrink: 0;
}

.user-info {
  flex: 1;
}

.user-title {
  font-size: 20px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 8px;
}

.user-desc {
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.6;
}

.pursuit-section {
  background: linear-gradient(135deg, #F0FDF4, #ECFDF5);
  padding: 48px;
  border-radius: 20px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
}

.pursuit-title {
  font-size: 28px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 32px;
  text-align: center;
}

.pursuit-items {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.pursuit-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  padding: 24px;
  background: white;
  border-radius: 16px;
  transition: all 0.3s;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.pursuit-item:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 24px rgba(0, 196, 140, 0.2);
}

.pursuit-icon {
  font-size: 40px;
}

.pursuit-text {
  font-size: 16px;
  font-weight: 600;
  color: var(--text-primary);
}

.solution-banner {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  border-radius: 20px;
  padding: 48px;
  box-shadow: 0 20px 60px rgba(0, 196, 140, 0.3);
}

.solution-content {
  display: flex;
  align-items: center;
  gap: 24px;
}

.solution-icon {
  font-size: 64px;
  animation: sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% {
    transform: scale(1) rotate(0deg);
  }
  50% {
    transform: scale(1.1) rotate(10deg);
  }
}

.solution-text h3 {
  font-size: 28px;
  font-weight: 700;
  color: white;
  margin-bottom: 8px;
}

.solution-text p {
  font-size: 16px;
  color: rgba(255, 255, 255, 0.9);
}

@media (max-width: 768px) {
  .pain-points {
    padding: 60px 0;
  }
  
  .carousel-content {
    min-height: 600px;
  }
  
  .carousel-dots {
    margin-top: 32px;
    gap: 10px;
  }
  
  .dot {
    width: 10px;
    height: 10px;
  }
  
  .dot.active {
    width: 28px;
  }
  
  .section-title {
    font-size: 28px;
  }
  
  .section-subtitle {
    font-size: 16px;
  }
  
  .pain-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .users-grid {
    grid-template-columns: 1fr;
  }
  
  .pursuit-items-large {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .pursuit-item-large {
    padding: 32px 24px;
  }
  
  .pursuit-icon-large {
    font-size: 48px;
  }
  
  .pursuit-text-large {
    font-size: 20px;
  }
  
  .pursuit-section {
    padding: 32px 24px;
  }
  
  .pursuit-title {
    font-size: 24px;
    margin-bottom: 24px;
  }
  
  .pursuit-items {
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }
  
  .solution-banner {
    padding: 32px 24px;
  }
  
  .solution-content {
    flex-direction: column;
    text-align: center;
  }
  
  .solution-text h3 {
    font-size: 22px;
  }
  
  .solution-text p {
    font-size: 14px;
  }
}
</style>
