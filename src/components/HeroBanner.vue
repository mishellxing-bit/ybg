<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">
            <span class="title-highlight">一句话</span>搞定复杂计算
            <br />
            智能处理Excel数据
          </h1>
          <p class="hero-description">
            通过自然语言对话，让不会函数的用户也能快速完成数据分析。
            <br />
            告别复杂公式，让AI成为您的Excel助手。
          </p>
          <div class="hero-buttons">
            <button class="btn-large btn-primary">
              <span>免费开始使用</span>
              <span class="arrow">→</span>
            </button>
            <button class="btn-large btn-secondary">观看演示</button>
          </div>
          <div class="hero-stats">
            <div class="stat-item">
              <div class="stat-number">100+</div>
              <div class="stat-label">用户信赖</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">10秒</div>
              <div class="stat-label">快速生成</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">0门槛</div>
              <div class="stat-label">上手即用</div>
            </div>
          </div>
        </div>
        <div class="hero-visual">
          <div class="demo-card">
            <div class="demo-chat">
              <div class="chat-bubble user">
                <span class="bubble-icon">💬</span>
                <span>计算销售额总和并生成柱状图</span>
              </div>
              <div class="chat-bubble ai">
                <span class="bubble-icon">🤖</span>
                <span>好的，已为您生成销售额分析图表</span>
              </div>
            </div>
            <div class="demo-chart">
              <div class="chart-bars">
                <div class="bar" style="height: 60%"></div>
                <div class="bar" style="height: 85%"></div>
                <div class="bar" style="height: 45%"></div>
                <div class="bar" style="height: 95%"></div>
                <div class="bar" style="height: 70%"></div>
              </div>
            </div>
          </div>
          <div class="floating-elements">
            <div class="float-item float-1">📈</div>
            <div class="float-item float-2">📊</div>
            <div class="float-item float-3">✨</div>
          </div>
        </div>
      </div>
    </div>
    <div class="hero-bg">
      <div class="bg-gradient-1"></div>
      <div class="bg-gradient-2"></div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
  position: relative;
  padding: 140px 0 80px;
  overflow: hidden;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-title {
  font-size: 48px;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 24px;
  color: var(--text-primary);
}

.title-highlight {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 18px;
  color: var(--text-secondary);
  margin-bottom: 40px;
  line-height: 1.8;
}

.hero-buttons {
  display: flex;
  gap: 16px;
  margin-bottom: 48px;
}

.btn-large {
  padding: 16px 32px;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 600;
  transition: all 0.3s;
  display: flex;
  align-items: center;
  gap: 8px;
}

.btn-primary {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  color: white;
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 30px rgba(102, 126, 234, 0.4);
}

.btn-primary .arrow {
  font-size: 20px;
  transition: transform 0.3s;
}

.btn-primary:hover .arrow {
  transform: translateX(4px);
}

.btn-secondary {
  background: white;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.btn-secondary:hover {
  background: var(--primary-color);
  color: white;
}

.hero-stats {
  display: flex;
  gap: 48px;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 32px;
  font-weight: 700;
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 14px;
  color: var(--text-secondary);
}

.hero-visual {
  position: relative;
}

.demo-card {
  background: white;
  border-radius: 20px;
  padding: 24px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.demo-chat {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 24px;
}

.chat-bubble {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 14px;
}

.chat-bubble.user {
  background: linear-gradient(135deg, #E0E7FF, #DDD6FE);
  align-self: flex-end;
  max-width: 80%;
}

.chat-bubble.ai {
  background: linear-gradient(135deg, #DBEAFE, #BFDBFE);
  align-self: flex-start;
  max-width: 80%;
}

.bubble-icon {
  font-size: 18px;
}

.demo-chart {
  background: linear-gradient(135deg, #F0F9FF, #E0F2FE);
  border-radius: 12px;
  padding: 20px;
  height: 200px;
}

.chart-bars {
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
  height: 100%;
  gap: 12px;
}

.bar {
  flex: 1;
  background: linear-gradient(180deg, var(--gradient-start), var(--gradient-end));
  border-radius: 8px 8px 0 0;
  animation: grow 1.5s ease-out;
}

@keyframes grow {
  from {
    height: 0 !important;
  }
}

.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.float-item {
  position: absolute;
  font-size: 40px;
  animation: floating 3s ease-in-out infinite;
}

.float-1 {
  top: 10%;
  right: -10%;
  animation-delay: 0s;
}

.float-2 {
  bottom: 20%;
  left: -10%;
  animation-delay: 1s;
}

.float-3 {
  top: 50%;
  right: -5%;
  animation-delay: 2s;
}

@keyframes floating {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
  }
  50% {
    transform: translateY(-30px) rotate(10deg);
  }
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  overflow: hidden;
}

.bg-gradient-1 {
  position: absolute;
  top: -50%;
  right: -20%;
  width: 800px;
  height: 800px;
  background: radial-gradient(circle, rgba(102, 126, 234, 0.15), transparent);
  animation: pulse 8s ease-in-out infinite;
}

.bg-gradient-2 {
  position: absolute;
  bottom: -50%;
  left: -20%;
  width: 800px;
  height: 800px;
  background: radial-gradient(circle, rgba(118, 75, 162, 0.15), transparent);
  animation: pulse 8s ease-in-out infinite;
  animation-delay: 4s;
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
    opacity: 0.5;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.8;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 100px 0 60px;
  }
  
  .hero-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .hero-title {
    font-size: 32px;
  }
  
  .hero-description {
    font-size: 16px;
  }
  
  .hero-buttons {
    flex-direction: column;
  }
  
  .hero-stats {
    gap: 24px;
  }
  
  .stat-number {
    font-size: 24px;
  }
}
</style>
