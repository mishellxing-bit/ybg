<template>
  <section class="cta-section">
    <div class="container">
      <div class="cta-content">
        <div class="cta-text">
          <h2 class="cta-title">准备好让数据分析变得简单了吗？</h2>
          <p class="cta-subtitle">加入易表格，体验自然语言处理Excel的魅力</p>
          <div class="cta-features">
            <div class="cta-feature">
              <span class="check-icon">✓</span>
              <span>无需学习复杂公式</span>
            </div>
            <div class="cta-feature">
              <span class="check-icon">✓</span>
              <span>10秒生成数据图表</span>
            </div>
            <div class="cta-feature">
              <span class="check-icon">✓</span>
              <span>免费开始使用</span>
            </div>
          </div>
          <button class="cta-button">
            <span>立即开始</span>
            <span class="arrow-icon">→</span>
          </button>
        </div>
        <div class="cta-visual">
          <div class="demo-window">
            <div class="window-header">
              <div class="window-dots">
                <span class="dot"></span>
                <span class="dot"></span>
                <span class="dot"></span>
              </div>
              <span class="window-title">易表格 AI助手</span>
            </div>
            <div class="window-content">
              <div class="demo-message ai">
                <div class="message-avatar">🤖</div>
                <div class="message-bubble">
                  <p>您好！我是易表格AI助手</p>
                  <p>请上传您的Excel文件或告诉我您想分析什么数据</p>
                </div>
              </div>
              <div class="demo-message user">
                <div class="message-bubble">
                  <p>帮我计算各月销售总额并生成趋势图</p>
                </div>
                <div class="message-avatar user-avatar">👤</div>
              </div>
              <div class="demo-message ai">
                <div class="message-avatar">🤖</div>
                <div class="message-bubble">
                  <p>好的，正在为您分析...</p>
                  <div class="typing-indicator">
                    <span></span>
                    <span></span>
                    <span></span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.cta-section {
  padding: 80px 0;
  background: linear-gradient(135deg, #667EEA 0%, #764BA2 100%);
  position: relative;
  overflow: hidden;
}

.cta-section::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -10%;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
  animation: float 8s ease-in-out infinite;
}

.cta-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.cta-title {
  font-size: 42px;
  font-weight: 700;
  color: white;
  margin-bottom: 20px;
  line-height: 1.3;
}

.cta-subtitle {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 32px;
}

.cta-features {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 40px;
}

.cta-feature {
  display: flex;
  align-items: center;
  gap: 12px;
  color: white;
  font-size: 16px;
}

.check-icon {
  width: 24px;
  height: 24px;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
}

.cta-button {
  background: white;
  color: var(--primary-color);
  padding: 18px 40px;
  border-radius: 12px;
  font-size: 18px;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 12px;
  transition: all 0.3s;
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.3);
}

.arrow-icon {
  font-size: 24px;
  transition: transform 0.3s;
}

.cta-button:hover .arrow-icon {
  transform: translateX(6px);
}

.demo-window {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  animation: float 6s ease-in-out infinite;
}

.window-header {
  background: #F3F4F6;
  padding: 12px 16px;
  display: flex;
  align-items: center;
  gap: 12px;
}

.window-dots {
  display: flex;
  gap: 6px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #D1D5DB;
}

.window-title {
  font-size: 14px;
  color: var(--text-secondary);
  font-weight: 500;
}

.window-content {
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  background: #FAFAFA;
  min-height: 300px;
}

.demo-message {
  display: flex;
  gap: 12px;
  animation: slideIn 0.5s ease-out;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.demo-message.user {
  flex-direction: row-reverse;
}

.message-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667EEA, #764BA2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  flex-shrink: 0;
}

.message-avatar.user-avatar {
  background: linear-gradient(135deg, #10B981, #059669);
}

.message-bubble {
  background: white;
  padding: 12px 16px;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  max-width: 80%;
}

.demo-message.user .message-bubble {
  background: linear-gradient(135deg, #E0E7FF, #DDD6FE);
}

.message-bubble p {
  margin: 0;
  font-size: 14px;
  color: var(--text-primary);
  line-height: 1.5;
}

.message-bubble p + p {
  margin-top: 8px;
}

.typing-indicator {
  display: flex;
  gap: 4px;
  padding: 8px 0;
}

.typing-indicator span {
  width: 8px;
  height: 8px;
  background: var(--primary-color);
  border-radius: 50%;
  animation: typing 1.4s ease-in-out infinite;
}

.typing-indicator span:nth-child(2) {
  animation-delay: 0.2s;
}

.typing-indicator span:nth-child(3) {
  animation-delay: 0.4s;
}

@keyframes typing {
  0%, 60%, 100% {
    transform: translateY(0);
    opacity: 0.7;
  }
  30% {
    transform: translateY(-10px);
    opacity: 1;
  }
}

@media (max-width: 768px) {
  .cta-section {
    padding: 60px 0;
  }
  
  .cta-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .cta-title {
    font-size: 28px;
  }
  
  .cta-subtitle {
    font-size: 16px;
  }
  
  .cta-button {
    padding: 14px 32px;
    font-size: 16px;
  }
}
</style>
