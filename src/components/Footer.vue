<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <div class="footer-logo">
            <span class="logo-icon">📊</span>
            <span class="logo-text">易表格</span>
          </div>
          <p class="footer-desc">让数据分析变得简单高效</p>
          <p class="footer-slogan">一句话搞定复杂计算</p>
        </div>
        <div class="footer-links">
          <div class="link-group">
            <h4 class="link-title">产品</h4>
            <a href="#" class="link-item">功能特点</a>
            <a href="#" class="link-item">使用案例</a>
            <a href="#" class="link-item">定价方案</a>
          </div>
          <div class="link-group">
            <h4 class="link-title">支持</h4>
            <a href="#" class="link-item">帮助中心</a>
            <a href="#" class="link-item">使用教程</a>
            <a href="#" class="link-item">联系我们</a>
          </div>
          <div class="link-group">
            <h4 class="link-title">关于</h4>
            <a href="#" class="link-item">关于我们</a>
            <a href="#" class="link-item">隐私政策</a>
            <a href="#" class="link-item">服务条款</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p class="copyright">© 2025 易表格. All rights reserved.</p>
        <div class="social-links">
          <a href="#" class="social-link">微信</a>
          <a href="#" class="social-link">微博</a>
          <a href="#" class="social-link">邮箱</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.footer {
  background: linear-gradient(180deg, #1F2937 0%, #111827 100%);
  color: white;
  padding: 60px 0 30px;
}

.footer-content {
  display: grid;
  grid-template-columns: 1.5fr 2fr;
  gap: 60px;
  margin-bottom: 48px;
  padding-bottom: 48px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 16px;
}

.logo-icon {
  font-size: 28px;
}

.footer-desc {
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 8px;
  font-size: 15px;
}

.footer-slogan {
  color: rgba(255, 255, 255, 0.5);
  font-size: 14px;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
}

.link-group {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.link-title {
  font-size: 16px;
  font-weight: 600;
  margin-bottom: 8px;
  color: white;
}

.link-item {
  color: rgba(255, 255, 255, 0.7);
  font-size: 14px;
  transition: color 0.3s;
}

.link-item:hover {
  color: white;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.copyright {
  color: rgba(255, 255, 255, 0.5);
  font-size: 14px;
}

.social-links {
  display: flex;
  gap: 24px;
}

.social-link {
  color: rgba(255, 255, 255, 0.7);
  font-size: 14px;
  transition: color 0.3s;
}

.social-link:hover {
  color: white;
}

@media (max-width: 768px) {
  .footer {
    padding: 40px 0 20px;
  }
  
  .footer-content {
    grid-template-columns: 1fr;
    gap: 32px;
    margin-bottom: 32px;
    padding-bottom: 32px;
  }
  
  .footer-links {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .footer-bottom {
    flex-direction: column;
    gap: 16px;
    text-align: center;
  }
}
</style>
