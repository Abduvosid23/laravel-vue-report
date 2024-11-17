<template>

    <div class="main-content">
        <h1 class="page-title">Transactions</h1>
    </div>
    <h1>Transactions</h1>
    <div class="transaction-list">
        <el-table :data="transactions" style="width: 100%">
            <!-- Date Column -->
            <el-table-column prop="date" label="Date" width="150">
                <template #default="{ row }">
                    <div class="date-group">
                        <div class="date">{{ row.date }}</div>
                        <div class="month">{{ row.month }}</div>
                    </div>
                </template>
            </el-table-column>

            <!-- Company Column -->
            <el-table-column prop="company" label="Company" width="250">
                <template #default="{ row }">
                    <div class="company-info">
                        <el-avatar :size="32" :src="row.logo" />
                        <span class="company-name">{{ row.company }}</span>
                    </div>
                </template>
            </el-table-column>

            <!-- Description Column -->
            <el-table-column prop="description" label="Description" />

            <!-- Amount Column -->
            <el-table-column prop="amount" label="Amount" width="150">
                <template #default="{ row }">
          <span :class="{ 'text-success': row.amount > 0, 'text-danger': row.amount < 0 }">
            {{ formatAmount(row.amount) }}
          </span>
                </template>
            </el-table-column>

            <!-- Schot Column -->
            <el-table-column prop="Schot" label="Status" width="120">
                <template #default="{ row }">
                    <el-tag :type="row.status === '000' ? 'info' : 'success'" size="small">
                        {{ row.status }}
                    </el-tag>
                </template>
            </el-table-column>

            <!-- Toggle Column -->
            <el-table-column width="80">
                <template #default="{ row }">
                    <el-switch v-model="row.isActive" />
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
export default {
    name: 'TransactionList',
    data() {
        return {
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
.transaction-list {
    padding: 20px;
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

:deep(.el-table) {
    --el-table-border-color: #EBEEF5;
    --el-table-header-bg-color: #F5F7FA;
}

:deep(.el-table th) {
    font-weight: 600;
}
</style>
