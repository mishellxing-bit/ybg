<template>
  <header class="header">
    <div class="container">
      <div class="header-content">
        <div class="logo">
          <span class="logo-icon">📊</span>
          <span class="logo-text">易表格</span>
        </div>
        <nav class="nav">
          <a href="#features" class="nav-link">功能特点</a>
          <a href="#users" class="nav-link">适用人群</a>
          <button class="btn-primary">立即体验</button>
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup>
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  z-index: 1000;
  padding: 16px 0;
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 24px;
  font-weight: 700;
  color: var(--primary-color);
}

.logo-icon {
  font-size: 28px;
}

.nav {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-link {
  color: var(--text-secondary);
  font-weight: 500;
  transition: color 0.3s;
}

.nav-link:hover {
  color: var(--primary-color);
}

.btn-primary {
  background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
  color: white;
  padding: 10px 24px;
  border-radius: 8px;
  font-weight: 500;
  transition: transform 0.3s, box-shadow 0.3s;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
}

@media (max-width: 768px) {
  .nav {
    gap: 16px;
  }
  
  .nav-link {
    font-size: 14px;
  }
  
  .btn-primary {
    padding: 8px 16px;
    font-size: 14px;
  }
}
</style>
