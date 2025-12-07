<template>
  <section id="features" class="features">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">强大功能，让数据分析更简单</h2>
        <p class="section-subtitle">通过自然语言对话，轻松完成复杂的数据分析任务</p>
      </div>
      <div class="features-grid">
        <div v-for="feature in features" :key="feature.id" class="feature-card">
          <div class="feature-header">
            <div class="feature-icon">{{ feature.icon }}</div>
            <div class="feature-badge">{{ feature.badge }}</div>
          </div>
          <h3 class="feature-title">{{ feature.title }}</h3>
          <p class="feature-desc">{{ feature.description }}</p>
          <div class="feature-highlights">
            <div v-for="(highlight, index) in feature.highlights" :key="index" class="highlight-item">
              <span class="highlight-dot">•</span>
              <span>{{ highlight }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  {
    id: 1,
    icon: '📤',
    badge: '智能上传',
    title: '自动处理Excel',
    description: '支持上传CSV和XLSX格式，上传文件后自动清洗表格数据',
    highlights: [
      '支持多个Excel文件上传',
      '每个Excel可支持多Sheet页',
      '文件可分组管理'
    ]
  },
  {
    id: 2,
    icon: '🧮',
    badge: '智能计算',
    title: '智能数据分析',
    description: '轻松完成从基础求和、平均值计算到复杂公式运算的所有操作',
    highlights: [
      '确保计算精度',
      '提供卓越的运算效率',
      '自然语言描述即可'
    ]
  },
  {
    id: 3,
    icon: '📊',
    badge: '可视化',
    title: '数据可视化图表',
    description: '输入指令词后，轻松创建图表，将数据转化为多种图表类型',
    highlights: [
      '支持简单图表柱状图、饼图、折线图等',
      '支持组合图表等多种类型',
      '10秒内获得专属图表'
    ]
  },
  {
    id: 4,
    icon: '🔄',
    badge: '灵活切换',
    title: '数据源随心切换',
    description: '让您数据切换灵活自如，支持随时切换数据源',
    highlights: [
      '新生成的数据表格可预览',
      '一键下载、保存',
      '快捷使用历史数据'
    ]
  },
  {
    id: 5,
    icon: '⚡',
    badge: '高效协同',
    title: '快捷指令分享',
    description: '让您高效分析，轻松协同，生成的图表或表格数据支持保存',
    highlights: [
      '自然语言保存为快捷指令',
      '执行快捷指令1s内出结果',
      '可分享指令给他人使用'
    ]
  },
  {
    id: 6,
    icon: '💻',
    badge: '代码透明',
    title: '代码追踪',
    description: '让您对数据处理有据可寻，生成的图表或表格数据支持代码追踪',
    highlights: [
      '代码复制、修改',
      '自主优化代码并保存',
      '让数据生成更便捷'
    ]
  }
]
</script>

<style scoped>
.features {
  padding: 80px 0;
  background: white;
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

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 32px;
}

.feature-card {
  background: linear-gradient(135deg, #FFFFFF 0%, #F9FAFB 100%);
  padding: 36px;
  border-radius: 20px;
  border: 1px solid var(--border-color);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.feature-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--gradient-start), var(--gradient-end));
  transform: scaleX(0);
  transition: transform 0.4s;
}

.feature-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
  border-color: var(--primary-light);
}

.feature-card:hover::before {
  transform: scaleX(1);
}

.feature-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}

.feature-icon {
  font-size: 48px;
  animation: bounce 2s ease-in-out infinite;
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.feature-badge {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  color: white;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
}

.feature-title {
  font-size: 24px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 12px;
}

.feature-desc {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 20px;
}

.feature-highlights {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
  color: var(--text-secondary);
}

.highlight-dot {
  color: var(--primary-color);
  font-weight: 700;
  font-size: 20px;
}

@media (max-width: 768px) {
  .features {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 28px;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .feature-card {
    padding: 28px;
  }
}
</style>
