<template>
    <div class="nav-container">
        <div class="navbar">
            <RouterLink
                v-for="nav in navs"
                :to="{ name: nav }"
                class="nav-btn"
            >
                {{ nav.charAt(0).toUpperCase() + nav.slice(1) }}
            </RouterLink>

            <button class="nav-theme-button" @click="toggleTheme">
                <Sun class="icon-sun" v-if="!theme" />
                <Moon class="icon-moon" v-else />
            </button>
        </div>
    </div>
</template>




<script setup lang="ts">
    import Moon from '@/assets/svg/Moon.vue'
    import Sun from '@/assets/svg/Sun.vue'
    import { useThemeStore } from '@/stores/theme'

    const themeStore = useThemeStore()
    const theme = computed(() => themeStore.theme)
    const toggleTheme = themeStore.toggleTheme

    const navs = ['about', 'projects', 'songs']
</script>

<style scoped>

/* Navbar Utama */
.navbar {
  background-color: #c9c8c7;
  position: fixed;
  bottom: 2rem;
  left: auto;
  right: auto;
  transform: translateX(-50%);
  padding: 10px 20px;
  border-radius: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  z-index: 100;
  transition: all 0.3s ease-in-out;
}

/* Dark Mode */
.dark .navbar {
  background-color: #282828;
}

/* Nav Button */
.nav-btn {
  font-family: 'KATSUMI', sans-serif ;
  letter-spacing: 1px;
  font-size: 18px;
  font-weight: bold;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 800px;
  color: #3d3b3c;
  transition: background 0.3s, color 0.3s;
}

.nav-btn:hover {
  background-color: #949392;
}

.dark .nav-btn {
  color: #f2f0ef;
}

.dark .nav-btn:hover {
  background-color: #3d3b3c;
}

/* Theme Toggle Button */
.nav-theme-button {
  background: transparent;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6px;
  border-radius: 50%;
  transition: background 0.3s ease;
  color: #3d3b3c;
}

.nav-theme-button:hover {
  background: #949392;
}

.dark .nav-theme-button {
  color: #f2f0ef;
}

.dark .nav-theme-button:hover {
  background: #3d3b3c;
}

@media (max-width: 768px) {
  .navbar {
    bottom: 3rem;
    right: auto;
    left: auto;
    padding: 8px 12px;
    border-radius: 30px;
    gap: 5px;
  }

  .nav-btn {
    font-size: 14px;
    padding: 6px 10px;
  }

  .nav-theme-button {
    padding: 5px;
    width: 36px;
    height: 36px;
  }
}


</style>
