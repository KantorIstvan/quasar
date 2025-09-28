<template>
  <q-page :style="{ backgroundColor: '#f8f9fa', minHeight: '100vh' }">
    <!-- Dashboard Header -->
    <div class="q-mb-xl">
      <h1 :style="{
        fontSize: '2rem',
        fontWeight: 'bold',
        color: '#343a40',
        marginBottom: '8px'
      }">
        Welcome to Dashboard
      </h1>
      <p :style="{ color: '#6c757d' }">Overview of your service management panel</p>
    </div>

    <!-- Dashboard Cards Grid -->
    <div class="row q-col-gutter-lg q-mb-xl">
      <!-- Service Packs Card -->
      <div class="col-12 col-md-6 col-lg-4">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white' }">
          <q-card-section :style="{ backgroundColor: '#495057', color: 'white' }">
            <div class="row items-center justify-between">
              <div>
                <h3 :style="{ fontSize: '18px', fontWeight: '600' }">Service Packs</h3>
                <p :style="{ color: '#bdc4ca', fontSize: '14px' }">Manage your services</p>
              </div>
              <q-icon name="inventory" size="32px" :style="{ color: '#85919d' }" />
            </div>
          </q-card-section>
          <q-card-section :style="{ backgroundColor: 'white' }">
            <div class="text-center q-py-md">
              <div :style="{
                fontSize: '3rem',
                fontWeight: 'bold',
                color: '#343a40',
                marginBottom: '8px'
              }">
                12
              </div>
              <p :style="{ color: '#6c757d' }">Active Packages</p>
            </div>
          </q-card-section>
          <q-card-actions :style="{ backgroundColor: '#eceef1', padding: '12px 16px' }">
            <q-btn
              flat
              label="View All"
              icon="arrow_forward"
              class="full-width"
              :style="{ color: '#495057' }"
            />
          </q-card-actions>
        </q-card>
      </div>

      <!-- Profile Card -->
      <div class="col-12 col-md-6 col-lg-4">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white' }">
          <q-card-section :style="{ backgroundColor: '#6c757d', color: 'white' }">
            <div class="row items-center justify-between">
              <div>
                <h3 :style="{ fontSize: '18px', fontWeight: '600' }">Profile</h3>
                <p :style="{ color: '#bdc4ca', fontSize: '14px' }">Account settings</p>
              </div>
              <q-icon name="person" size="32px" :style="{ color: '#85919d' }" />
            </div>
          </q-card-section>
          <q-card-section :style="{ backgroundColor: 'white' }">
            <div class="q-py-md">
              <div class="row items-center q-gutter-sm q-mb-sm">
                <q-avatar size="48px" :style="{ backgroundColor: '#495057', color: 'white' }">JD</q-avatar>
                <div>
                  <p :style="{ fontWeight: '600', color: '#343a40' }">John Doe</p>
                  <p :style="{ color: '#6c757d', fontSize: '14px' }">Administrator</p>
                </div>
              </div>
            </div>
          </q-card-section>
          <q-card-actions :style="{ backgroundColor: '#eceef1', padding: '12px 16px' }">
            <q-btn
              flat
              label="Edit Profile"
              icon="edit"
              class="full-width"
              :style="{ color: '#495057' }"
            />
          </q-card-actions>
        </q-card>
      </div>

      <!-- Subscriptions Card -->
      <div class="col-12 col-md-6 col-lg-4">
        <q-card class="shadow-4" :style="{ backgroundColor: 'white' }">
          <q-card-section :style="{ backgroundColor: '#202327', color: 'white' }">
            <div class="row items-center justify-between">
              <div>
                <h3 :style="{ fontSize: '18px', fontWeight: '600' }">Subscriptions</h3>
                <p :style="{ color: '#bdc4ca', fontSize: '14px' }">Manage subscriptions</p>
              </div>
              <q-icon name="subscriptions" size="32px" :style="{ color: '#85919d' }" />
            </div>
          </q-card-section>
          <q-card-section :style="{ backgroundColor: 'white' }">
            <div class="text-center q-py-md">
              <div :style="{
                fontSize: '3rem',
                fontWeight: 'bold',
                color: '#343a40',
                marginBottom: '8px'
              }">
                5
              </div>
              <p :style="{ color: '#6c757d' }">Active Subscriptions</p>
            </div>
          </q-card-section>
          <q-card-actions :style="{ backgroundColor: '#eceef1', padding: '12px 16px' }">
            <q-btn
              flat
              label="Manage"
              icon="settings"
              class="full-width"
              :style="{ color: '#495057' }"
            />
          </q-card-actions>
        </q-card>
      </div>
    </div>

    <!-- Recent Activity Section -->
    <q-card class="shadow-4 q-mb-lg" :style="{ backgroundColor: 'white' }">
      <q-card-section class="q-pa-lg">
        <h2 class="row items-center q-gutter-sm q-mb-md" :style="{
          fontSize: '20px',
          fontWeight: 'bold',
          color: '#343a40',
          margin: 0
        }">
          <q-icon name="history" :style="{ color: '#6c757d' }" />
          Recent Activity
        </h2>

        <q-list separator :style="{ backgroundColor: 'white' }">
          <q-item class="q-px-none">
            <q-item-section avatar>
              <q-avatar size="40px" :style="{ backgroundColor: '#8c959f' }">
                <q-icon name="add" :style="{ color: 'white' }" />
              </q-avatar>
            </q-item-section>
            <q-item-section>
              <q-item-label :style="{ color: '#343a40', fontWeight: '500' }">New service pack created</q-item-label>
              <q-item-label caption :style="{ color: '#6c757d' }">Premium Package - 2 hours ago</q-item-label>
            </q-item-section>
            <q-item-section side>
              <q-chip size="sm" :style="{ backgroundColor: '#b2b9bf', color: 'white' }">New</q-chip>
            </q-item-section>
          </q-item>

          <q-item class="q-px-none">
            <q-item-section avatar>
              <q-avatar size="40px" :style="{ backgroundColor: '#a7adb2' }">
                <q-icon name="person_add" :style="{ color: 'white' }" />
              </q-avatar>
            </q-item-section>
            <q-item-section>
              <q-item-label :style="{ color: '#343a40', fontWeight: '500' }">Profile updated</q-item-label>
              <q-item-label caption :style="{ color: '#6c757d' }">Contact information changed - 5 hours ago</q-item-label>
            </q-item-section>
          </q-item>

          <q-item class="q-px-none">
            <q-item-section avatar>
              <q-avatar size="40px" :style="{ backgroundColor: '#58626c' }">
                <q-icon name="payment" :style="{ color: 'white' }" />
              </q-avatar>
            </q-item-section>
            <q-item-section>
              <q-item-label :style="{ color: '#343a40', fontWeight: '500' }">Subscription renewed</q-item-label>
              <q-item-label caption :style="{ color: '#6c757d' }">Monthly plan - 1 day ago</q-item-label>
            </q-item-section>
            <q-item-section side>
              <q-chip size="sm" :style="{ backgroundColor: '#4caf50', color: 'white' }">Paid</q-chip>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Quick Actions -->
    <q-card class="shadow-4" :style="{ backgroundColor: 'white' }">
      <q-card-section class="q-pa-lg">
        <h2 :style="{
          fontSize: '20px',
          fontWeight: 'bold',
          color: '#343a40',
          marginBottom: '16px'
        }">
          Quick Actions
        </h2>
        <div class="row q-gutter-sm">
          <q-btn
            icon="add"
            label="Add Service Pack"
            :style="{ backgroundColor: '#495057', color: 'white' }"
          />
          <q-btn
            icon="person_add"
            label="New User"
            :style="{ backgroundColor: '#6c757d', color: 'white' }"
          />
          <q-btn
            icon="analytics"
            label="View Reports"
            :style="{ backgroundColor: '#343a40', color: 'white' }"
          />
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'IndexPage',

  setup() {
    return {};
  },
});
</script>
