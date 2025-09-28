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
        Profile
      </h1>
      <p :style="{ color: '#6c757d' }">Manage your account information</p>
    </div>

    <!-- Profile Content -->
    <div class="col q-col-gutter-lg">
      <!-- Profile Overview Card -->
      <div class="col-12 col-md-4">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white', height: '100%' }">
          <q-card-section class="text-left q-pa-xl">
            <!-- Avatar Placeholder -->
            <div class="q-mb-md">
              <q-avatar
                size="120px"
                :style="{
                  backgroundColor: 'gray',
                  color: 'white',
                  fontSize: '3rem',
                  fontWeight: 'bold'
                }"
              >
                {{ getInitials(userProfile.name) }}
              </q-avatar>
            </div>

            <!-- Name -->
            <div :style="{
              fontSize: '1.75rem',
              fontWeight: 'bold',
              color: '#343a40',
              marginBottom: '8px'
            }">
              {{ userProfile.name }}
            </div>

            <!-- Role Badge -->
            <q-chip
              :style="{
                backgroundColor: '#e3f2fd',
                color: '#1976d2',
                fontWeight: '600'
              }"
              :label="userProfile.role"
              size="md"
            />
          </q-card-section>
        </q-card>
      </div>

      <!-- Profile Details Card -->
      <div class="col-12 col-md-8">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white', height: '100%' }">
          <q-card-section class="q-pa-xl">
            <div class="text-h6 q-mb-lg" :style="{ color: '#343a40', fontWeight: 'bold' }">
              Personal Information
            </div>

            <div class="q-gutter-lg">
              <!-- Email Field -->
              <div class="profile-field">
                <div class="profile-label">
                  <q-icon name="email" :style="{ marginRight: '8px', color: '#6c757d' }" />
                  Email Address
                </div>
                <div class="profile-value">{{ userProfile.email }}</div>
              </div>

              <!-- Role Field -->
              <div class="profile-field">
                <div class="profile-label">
                  <q-icon name="person" :style="{ marginRight: '8px', color: '#6c757d' }" />
                  Role
                </div>
                <div class="profile-value">{{ userProfile.role }}</div>
              </div>

              <!-- Password Field -->
              <div class="profile-field">
                <div class="profile-label">
                  <q-icon name="lock" :style="{ marginRight: '8px', color: '#6c757d' }" />
                  Password
                </div>
                <div class="profile-value">{{ userProfile.password }}</div>
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

interface UserProfile {
  name: string
  email: string
  role: string
  password: string
}

const userProfile = ref<UserProfile>({
  name: 'John Doe',
  email: 'john.doe@example.com',
  role: 'Admin',
  password: '********'
})

const getInitials = (name: string): string => {
  return name
    .split(' ')
    .map(word => word.charAt(0))
    .join('')
    .toUpperCase()
}
</script>

<style scoped>
.profile-field {
  padding: 16px 0;
  border-bottom: 1px solid #f1f3f4;
}

.profile-field:last-child {
  border-bottom: none;
}

.profile-label {
  font-size: 0.875rem;
  color: #6c757d;
  margin-bottom: 8px;
  font-weight: 600;
  display: flex;
  align-items: center;
}

.profile-value {
  font-size: 1.1rem;
  color: #343a40;
  font-weight: 500;
  padding-left: 24px;
}
</style>
