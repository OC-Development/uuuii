<template>
  <div id="app">
    <header class="app-header">
      <h1>مشروع واجهة المستخدم</h1>
      <nav>
        <button @click="currentView = 'dashboard'" :class="{ active: currentView === 'dashboard' }">
          لوحة التحكم
        </button>
        <button @click="currentView = 'calendar'" :class="{ active: currentView === 'calendar' }">
          التقويم
        </button>
        <button @click="currentView = 'map'" :class="{ active: currentView === 'map' }">
          الخريطة
        </button>
      </nav>
    </header>

    <main class="app-main">
      <DashboardView v-if="currentView === 'dashboard'" />
      <CalendarView v-if="currentView === 'calendar'" />
      <MapView v-if="currentView === 'map'" />
    </main>

    <footer class="app-footer">
      <p>&copy; 2025 مشروع واجهة المستخدم. جميع الحقوق محفوظة.</p>
    </footer>
  </div>
</template>

<script>
import DashboardView from './components/DashboardView.vue'
import CalendarView from './components/CalendarView.vue'
import MapView from './components/MapView.vue'

export default {
  name: 'App',
  components: {
    DashboardView,
    CalendarView,
    MapView
  },
  data() {
    return {
      currentView: 'dashboard'
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Geist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  direction: rtl;
  text-align: right;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.app-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 1rem 2rem;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.app-header h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.app-header nav {
  display: flex;
  gap: 1rem;
}

.app-header nav button {
  background: rgba(255,255,255,0.2);
  border: none;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.app-header nav button:hover {
  background: rgba(255,255,255,0.3);
  transform: translateY(-2px);
}

.app-header nav button.active {
  background: rgba(255,255,255,0.4);
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.app-main {
  flex: 1;
  padding: 2rem;
  background: #f8fafc;
}

.app-footer {
  background: #2d3748;
  color: white;
  text-align: center;
  padding: 1rem;
}
</style>