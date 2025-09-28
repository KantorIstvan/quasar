<template>
  <q-layout view="lHh Lpr lFf" :style="{ backgroundColor: '#f8f9fa' }">
    <!-- Header -->
    <q-header :style="{ backgroundColor: '#343a40' }" class="shadow-3">
      <q-toolbar :style="{ color: '#f8f9fa' }">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
          :style="{ color: '#f8f9fa' }"
        />

        <q-toolbar-title :style="{ color: '#f8f9fa', fontWeight: '600' }">
          Dashboard
        </q-toolbar-title>

        <!-- Login/Username section -->
        <div class="row items-center q-gutter-md">
          <div v-if="isLoggedIn" class="row items-center q-gutter-sm">
            <q-avatar size="32px" :style="{ backgroundColor: '#6c757d', color: 'white' }">
              <q-icon name="person" />
            </q-avatar>
            <span :style="{ color: '#f8f9fa', fontWeight: '500' }">{{ username }}</span>
          </div>
          <q-btn
            v-else
            flat
            label="Login"
            icon="login"
            :style="{ backgroundColor: '#495057', color: '#f8f9fa' }"
            @click="handleLogin"
          />
        </div>
      </q-toolbar>
    </q-header>

    <!-- Sidebar Drawer -->
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="280"
      :style="{ backgroundColor: '#15171a' }"
    >
      <div class="column full-height">
        <!-- Sidebar Header -->
        <div class="q-pa-lg" :style="{ borderBottom: '1px solid #2a2f34' }">
          <div class="row items-center q-gutter-sm">
            <q-avatar size="48px" :style="{ backgroundColor: '#6c757d' }">
              <q-icon name="dashboard" :style="{ color: '#f8f9fa' }" />
            </q-avatar>
            <div>
              <div :style="{ color: '#f8f9fa', fontSize: '18px', fontWeight: 'bold' }">Dashboard</div>
              <div :style="{ color: '#adb5bd', fontSize: '14px' }">Management Panel</div>
            </div>
          </div>
        </div>

        <!-- Navigation Links -->
        <div class="col q-py-md">
          <q-list :style="{ color: '#f8f9fa' }">
            <q-item
              clickable
              v-ripple
              :class="getNavItemClass('service-packs')"
              @click="navigateTo('service-packs')"
              class="q-mx-sm rounded-borders"
            >
              <q-item-section avatar>
                <q-icon name="inventory" :style="{ color: '#adb5bd' }" />
              </q-item-section>
              <q-item-section>
                <q-item-label :style="{ fontWeight: '500' }">Service Packs</q-item-label>
                <q-item-label caption :style="{ color: '#85919d' }">
                  Manage service packages
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-item
              clickable
              v-ripple
              :class="getNavItemClass('profile')"
              @click="navigateTo('profile')"
              class="q-mx-sm rounded-borders"
            >
              <q-item-section avatar>
                <q-icon name="person" :style="{ color: '#adb5bd' }" />
              </q-item-section>
              <q-item-section>
                <q-item-label :style="{ fontWeight: '500' }">Profile</q-item-label>
                <q-item-label caption :style="{ color: '#85919d' }">
                  Account settings
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-item
              clickable
              v-ripple
              :class="getNavItemClass('subscriptions')"
              @click="navigateTo('subscriptions')"
              class="q-mx-sm rounded-borders"
            >
              <q-item-section avatar>
                <q-icon name="subscriptions" :style="{ color: '#adb5bd' }" />
              </q-item-section>
              <q-item-section>
                <q-item-label :style="{ fontWeight: '500' }">Subscriptions</q-item-label>
                <q-item-label caption :style="{ color: '#85919d' }">
                  Manage subscriptions
                </q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </div>

        <!-- Logout Button at Bottom -->
        <div class="q-pa-md" :style="{ borderTop: '1px solid #2a2f34' }">
          <q-btn
            v-if="isLoggedIn"
            flat
            icon="logout"
            label="Logout"
            class="full-width"
            :style="{
              backgroundColor: '#dc3545',
              color: '#f8f9fa',
              justifyContent: 'flex-start'
            }"
            @click="handleLogout"
          />
        </div>
      </div>
    </q-drawer>

    <!-- Main Content Area -->
    <q-page-container :style="{ backgroundColor: '#f8f9fa' }">
      <div class="q-pa-lg">
        <router-view />
      </div>
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import { useRouter, useRoute } from 'vue-router';

export default defineComponent({
  name: 'MainLayout',

  setup() {
    const router = useRouter();
    const route = useRoute();
    const leftDrawerOpen = ref(false);
    const isLoggedIn = ref(true); // Simulate logged in state
    const username = ref('John Doe');

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    const handleLogin = () => {
      // Handle login logic
      console.log('Login clicked');
    };

    const handleLogout = () => {
      // Handle logout logic
      isLoggedIn.value = false;
      username.value = '';
      console.log('Logout clicked');
    };

    const navigateTo = (routeName: string) => {
      router.push(`/${routeName}`).catch((err) => {
        console.error('Navigation error:', err);
      });
    };

    const getNavItemClass = computed(() => (routeName: string) => {
      const currentPath = route.path.substring(1) || 'dashboard'; // Remove leading slash
      const isActive = currentPath === routeName || (routeName === 'service-packs' && currentPath === '');

      if (isActive) {
        return 'nav-item-active';
      }
      return 'nav-item-inactive';
    });

    return {
      leftDrawerOpen,
      isLoggedIn,
      username,
      toggleLeftDrawer,
      handleLogin,
      handleLogout,
      navigateTo,
      getNavItemClass,
    };
  },
});
</script>

<style scoped>
.nav-item-active {
  background-color: #495057 !important;
  color: #f8f9fa !important;
}

.nav-item-inactive {
  color: #adb5bd !important;
}

.nav-item-inactive:hover {
  background-color: #202327 !important;
}

.q-item {
  min-height: 56px;
}
</style>
