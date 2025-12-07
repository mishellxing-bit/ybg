<template>
  <section id="users" class="target-users">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">为谁而设计？</h2>
        <p class="section-subtitle">专为需要高效处理Excel但不想学习复杂公式的人群打造</p>
      </div>
      <div class="users-content">
        <div class="users-grid">
          <div v-for="user in users" :key="user.id" class="user-card">
            <div class="user-icon">{{ user.icon }}</div>
            <div class="user-info">
              <h3 class="user-title">{{ user.title }}</h3>
              <p class="user-desc">{{ user.description }}</p>
            </div>
          </div>
        </div>
        <div class="pursuit-section">
          <h3 class="pursuit-title">他们追求什么？</h3>
          <div class="pursuit-items">
            <div class="pursuit-item">
              <span class="pursuit-icon">⚡</span>
              <span class="pursuit-text">效率至上</span>
            </div>
            <div class="pursuit-item">
              <span class="pursuit-icon">✨</span>
              <span class="pursuit-text">简洁易用</span>
            </div>
            <div class="pursuit-item">
              <span class="pursuit-icon">📊</span>
              <span class="pursuit-text">快速洞察</span>
            </div>
            <div class="pursuit-item">
              <span class="pursuit-icon">🎯</span>
              <span class="pursuit-text">精准分析</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
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
</script>

<style scoped>
.target-users {
  padding: 100px 0;
  background: linear-gradient(180deg, #FFFFFF 0%, #F9FAFB 100%);
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
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
  background: linear-gradient(135deg, #F0F9FF, #E0F2FE);
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
  box-shadow: 0 8px 24px rgba(102, 126, 234, 0.2);
}

.pursuit-icon {
  font-size: 40px;
}

.pursuit-text {
  font-size: 16px;
  font-weight: 600;
  color: var(--text-primary);
}

@media (max-width: 768px) {
  .target-users {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 28px;
  }
  
  .users-content {
    gap: 32px;
  }
  
  .users-grid {
    grid-template-columns: 1fr;
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
}
</style>
