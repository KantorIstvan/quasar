<template>
  <q-page :style="{ backgroundColor: '#f8f9fa', minHeight: '100vh' }">
    <!-- Page Header -->
    <div class="q-mb-xl">
      <h1 :style="{
        fontSize: '2rem',
        fontWeight: 'bold',
        color: '#343a40',
        marginBottom: '8px'
      }">
        Subscriptions
      </h1>
      <p :style="{ color: '#6c757d' }">View and manage your active subscriptions</p>
    </div>

    <!-- Subscriptions Table -->
    <q-card class="shadow-4" :style="{ backgroundColor: 'white' }">
      <q-table
        :rows="subscriptions"
        :columns="columns"
        row-key="id"
        :style="{ backgroundColor: 'white' }"
        :rows-per-page-options="[10, 25, 50]"
      >
        <template v-slot:body-cell-status="props">
          <q-td :props="props">
            <q-chip
              :color="getStatusColor(props.value)"
              text-color="white"
              :label="props.value"
              size="sm"
            />
          </q-td>
        </template>

        <template v-slot:body-cell-startDate="props">
          <q-td :props="props">
            {{ formatDate(props.value) }}
          </q-td>
        </template>

        <template v-slot:body-cell-endDate="props">
          <q-td :props="props">
            {{ formatDate(props.value) }}
          </q-td>
        </template>
      </q-table>
    </q-card>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { date } from 'quasar'

interface Subscription {
  id: string
  startDate: string
  endDate: string
  servicePackName: string
  status: 'Active' | 'Expired' | 'Pending' | 'Cancelled'
}

const columns = [
  {
    name: 'startDate',
    required: true,
    label: 'Start Date',
    align: 'left' as const,
    field: 'startDate',
    sortable: true
  },
  {
    name: 'endDate',
    required: true,
    label: 'End Date',
    align: 'left' as const,
    field: 'endDate',
    sortable: true
  },
  {
    name: 'servicePackName',
    required: true,
    label: 'Service Pack Name',
    align: 'left' as const,
    field: 'servicePackName',
    sortable: true
  },
  {
    name: 'status',
    required: true,
    label: 'Status',
    align: 'center' as const,
    field: 'status',
    sortable: true
  }
]

const subscriptions = ref<Subscription[]>([
  {
    id: '1',
    startDate: '2024-01-15',
    endDate: '2024-12-15',
    servicePackName: 'Premium Support',
    status: 'Active'
  },
  {
    id: '2',
    startDate: '2023-08-01',
    endDate: '2024-08-01',
    servicePackName: 'Basic Support',
    status: 'Active'
  },
  {
    id: '3',
    startDate: '2024-03-10',
    endDate: '2024-06-10',
    servicePackName: 'Training Package',
    status: 'Expired'
  },
  {
    id: '4',
    startDate: '2024-09-01',
    endDate: '2024-12-01',
    servicePackName: 'Development Package',
    status: 'Active'
  },
  {
    id: '5',
    startDate: '2024-10-01',
    endDate: '2025-10-01',
    servicePackName: 'Enterprise Support',
    status: 'Pending'
  },
  {
    id: '6',
    startDate: '2023-05-15',
    endDate: '2024-05-15',
    servicePackName: 'Maintenance Package',
    status: 'Cancelled'
  }
])

const getStatusColor = (status: string) => {
  switch (status) {
    case 'Active':
      return 'green'
    case 'Expired':
      return 'red'
    case 'Pending':
      return 'orange'
    case 'Cancelled':
      return 'grey'
    default:
      return 'grey'
  }
}

const formatDate = (dateString: string) => {
  return date.formatDate(dateString, 'MMM DD, YYYY')
}
</script>
