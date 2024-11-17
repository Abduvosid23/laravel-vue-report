<template>
  <div class="transaction-app">
    <!-- Navbar -->
    <el-menu
        :default-active="activeIndex"
        class="navbar"
        mode="horizontal"
        @select="handleSelect"
    >
      <el-menu-item index="transactions">Transactions</el-menu-item>
      <el-menu-item index="analytics">Analytics</el-menu-item>
      <el-menu-item index="settings">Settings</el-menu-item>

      <div class="flex-grow" />

      <el-menu-item index="profile" class="profile-menu">
        <el-avatar :size="32" :src="userAvatar" />
        <span class="username">John Doe</span>
      </el-menu-item>
    </el-menu>

    <!-- Main Content Area -->

  </div>
</template>

<script>
export default {
  name: 'TransactionApp',
  data() {
    return {
      activeIndex: 'transactions',
      userAvatar: '/placeholder.svg?height=32&width=32',
      transactions: [
        {
          date: '7',
          month: 'ноября 2023',
          logo: '/placeholder.svg?height=32&width=32',
          company: 'ООО "ЦЕНТР"',
          description: 'Предпринимательская выплата',
          amount: -5488.5,
          status: 'DOD',
          isActive: true
        },
        {
          date: '6',
          month: 'ноября 2023',
          logo: '/placeholder.svg?height=32&width=32',
          company: 'ООО "НЕФТЬ"',
          description: 'Предпринимательская поступления',
          amount: 4275.0,
          status: 'DOD',
          isActive: true
        },
        {
          date: '6',
          month: 'ноября 2023',
          logo: '/placeholder.svg?height=32&width=32',
          company: 'ЗТК "Маркет"',
          description: 'Предпринимательская поступления',
          amount: 10988.8,
          status: 'DOD',
          isActive: true
        }
      ]
    }
  },
  methods: {
    handleSelect(key) {
      this.activeIndex = key
      console.log('Selected:', key)
    },
    formatAmount(amount) {
      return new Intl.NumberFormat('ru-RU', {
        style: 'currency',
        currency: 'RUB'
      }).format(amount)
    }
  }
}
</script>

<style scoped>
.transaction-app {
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
}

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  display: flex;
  border-bottom: 1px solid var(--el-border-color-light);
  padding: 0 20px;
}

.flex-grow {
  flex-grow: 1;
}

.profile-menu {
  display: flex;
  align-items: center;
}

.username {
  margin-left: 10px;
  font-weight: 500;
}

.main-content {
  padding-top: 60px; /* To account for the fixed navbar */
  padding: 80px 20px 20px;
}

.page-title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 20px;
  color: var(--el-text-color-primary);
}

.transaction-list {
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
}

.date-group {
  display: flex;
  flex-direction: column;
}

.date {
  font-size: 16px;
  font-weight: bold;
}

.month {
  font-size: 12px;
  color: #909399;
}

.company-info {
  display: flex;
  align-items: center;
  gap: 12px;
}

.company-name {
  font-weight: 500;
}

.text-success {
  color: #67C23A;
}

.text-danger {
  color: #F56C6C;
}

:deep(.el-menu--horizontal > .el-menu-item) {
  height: 60px;
  line-height: 60px;
  border-bottom: none;
}

:deep(.el-menu--horizontal > .el-menu-item.is-active) {
  border-bottom: 2px solid var(--el-color-primary);
  color: var(--el-color-primary);
}

:deep(.el-table) {
  --el-table-border-color: #EBEEF5;
  --el-table-header-bg-color: #F5F7FA;
}

:deep(.el-table th) {
  font-weight: 600;
}
</style>
