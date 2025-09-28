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
        Service Packs
      </h1>
      <p :style="{ color: '#6c757d' }">Browse and select from our available service packages</p>
    </div>

    <!-- Service Pack Cards -->
    <div class="row q-col-gutter-lg">
      <div v-for="pack in servicePacks" :key="pack.id" class="col-12 col-md-6 col-lg-4">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white', height: '100%', display: 'flex', flexDirection: 'column' }">
          <q-card-section class="q-pa-lg" :style="{ flex: '1', display: 'flex', flexDirection: 'column' }">
            <div class="text-h6 q-mb-sm" :style="{ color: '#343a40', fontWeight: 'bold' }">
              {{ pack.name }}
            </div>
            <div class="text-caption q-mb-md" :style="{ color: '#6c757d' }">
              ID: {{ pack.id }}
            </div>
            <p :style="{ color: '#495057', lineHeight: '1.5', marginBottom: '16px', flex: '1' }">
              {{ pack.description }}
            </p>
            <div :style="{ marginTop: 'auto' }">
              <div class="text-h6" :style="{ color: '#28a745', fontWeight: 'bold' }">
                ${{ pack.price }}
              </div>
              <div class="text-caption" :style="{ color: '#6c757d' }">
                {{ pack.duration }}
              </div>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface ServicePack {
  id: string
  name: string
  description: string
  price: number
  duration: string
}

const servicePacks = ref<ServicePack[]>([
  {
    id: 'SP001',
    name: 'Basic Support',
    description: 'Essential support services including email assistance, basic troubleshooting, and documentation access.',
    price: 99,
    duration: 'Monthly'
  },
  {
    id: 'SP002',
    name: 'Premium Support',
    description: 'Comprehensive support with priority response, phone support, and advanced technical assistance.',
    price: 249,
    duration: 'Monthly'
  },
  {
    id: 'SP003',
    name: 'Enterprise Support',
    description: 'Full enterprise-grade support with dedicated account manager, 24/7 availability, and custom solutions.',
    price: 599,
    duration: 'Monthly'
  },
  {
    id: 'SP004',
    name: 'Development Package',
    description: 'Specialized package for developers including API access, development tools, and technical documentation.',
    price: 199,
    duration: 'Monthly'
  },
  {
    id: 'SP005',
    name: 'Training Package',
    description: 'Complete training solution with online courses, certification programs, and hands-on workshops.',
    price: 399,
    duration: '3 Months'
  },
  {
    id: 'SP006',
    name: 'Maintenance Package',
    description: 'Regular system maintenance, updates, security patches, and performance optimization services.',
    price: 149,
    duration: 'Monthly'
  }
])
</script>
