<template>
  <div class="sidebar-container">
    <!-- Toggle Button -->
    <button
      @click="toggleSidebar"
      class="sidebar-toggle"
      :class="{ 'sidebar-open': isOpen }"
      aria-label="Toggle sidebar"
    >
      <span class="toggle-icon">
        <p v-if="!isOpen">☰</p>
        <p v-else>✕</p>
      </span>
    </button>

    <!-- Sidebar Overlay (for mobile) -->
    <div
      v-if="isOpen"
      class="sidebar-overlay"
      @click="closeSidebar"
    ></div>

    <!-- Sidebar -->
    <div class="sidebar" :class="{ 'sidebar-open': isOpen }">
      <div class="sidebar-header">
      </div>

      <nav class="sidebar-nav">
        <ul class="nav-list">
          <li class="nav-item">
            <a href="#home" class="nav-link" :class="{ active: activeSection === 'home' }" @click="setActive('home')">
              
              Home
            </a>
          </li>
          <li class="nav-item">
            <a href="#about" class="nav-link" :class="{ active: activeSection === 'about' }" @click="setActive('about')">
              
              About Me/Projects
            </a>
          </li>
          
        
          <li class="nav-item">
            <a href="#news" class="nav-link" title="WIP">
              
              News/Updates
             
            </a>
          </li>
        </ul>
      </nav>
      <div class="cyrene">
        <img src="../assets/agnes.gif" width="300px"/>
      </div>
     
        </div>
      </div>

</template>

<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['navigate'])

const isOpen = ref(false)
const activeSection = ref('home')

const toggleSidebar = () => {
  isOpen.value = !isOpen.value
}

const closeSidebar = () => {
  isOpen.value = false
}

const setActive = (section) => {
  activeSection.value = section
  closeSidebar()

  // For contact and news, emit navigate event instead of scrolling
  if (section === 'contact' || section === 'news') {
    emit('navigate', section)
  } else {
    // Smooth scroll to section
    const element = document.querySelector(`#${section}`)
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' })
    }
  }
}

// Close sidebar when clicking outside on mobile
onMounted(() => {
  const handleClickOutside = (e) => {
    if (window.innerWidth <= 768 && isOpen.value) {
      const sidebar = document.querySelector('.sidebar')
      const toggle = document.querySelector('.sidebar-toggle')
      if (sidebar && toggle && !sidebar.contains(e.target) && !toggle.contains(e.target)) {
        closeSidebar()
      }
    }
  }

  document.addEventListener('click', handleClickOutside)
})
</script>

<style scoped>
.sidebar-container {
  position: relative;
  z-index: 1000;
}

/* Toggle Button */
.sidebar-toggle {
  position: fixed;
  top: 20px;
  left: 20px;
  z-index: 1001;
  background: linear-gradient(135deg, #acd7fa 0%, #e4bbff 100%);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transition: all 0.3s ease;
  color: white;
  font-size: 1.2rem;
}

.sidebar-toggle:hover {
  transform: scale(1.);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
}

.sidebar-toggle.sidebar-open {
  background: linear-gradient(135deg,  #acd7fa 0%, #e4bbff 100%);
}

/* Sidebar Overlay */
.sidebar-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
  display: none;
}

/* Sidebar */
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  width: 250px;
  background: linear-gradient(135deg, #4da9ff 0%, #d997ff 100%);
  color: white;
  padding: 20px 0;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transform: translateX(-100%);
  transition: transform 0.3s ease;
  z-index: 1000;
  display: flex;
  flex-direction: column;
}

.sidebar.sidebar-open {
  transform: translateX(0);
}

.sidebar-header {
  margin-top: 50px; 
}


.sidebar-nav {
  flex: 1;
  padding: 20px 0;
}

.nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.nav-item {
    
  margin-bottom: 5px;
  font-family: 'CustomFont';
}

.nav-link {
  display: flex;
  align-items: center;
  padding: 15px 20px;
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: all 0.3s ease;
  border-radius: 0 25px 25px 0;
  margin-right: 10px;
}

.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.1);
  color: white;
  transform: translateY(-10px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
  border-radius: 0px 20px 20px 0px;

}




/* Responsive design */
@media (max-width: 768px) {
  .sidebar-overlay {
    display: block;
  }

  .sidebar {
    width: 280px;
  }

  .sidebar-toggle {
    top: 15px;
    left: 15px;
    width: 45px;
    height: 45px;
    font-size: 1rem;
  }

  .sidebar-header {
    margin-top: 60px;
  }

  .sidebar-title {
    font-size: 1.3rem;
  }

  .nav-link {
    padding: 15px 20px;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .sidebar {
    width: 100%;
  }

  .sidebar-toggle {
    width: 40px;
    height: 40px;
    font-size: 0.9rem;
  }
}
</style>