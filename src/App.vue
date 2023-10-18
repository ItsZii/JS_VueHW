<template>
  <div id="app">
    <HeaderComponent @loginStatusChanged="updateLoginStatus" />
    <div class="content-container" v-if="loggedIn">
      <div class="nav-container">
        <NavigationComponent @tabChanged="updateActiveTab" />
      </div>
      <div class="main-container">
        <HomeComponent v-if="activeTab === 'HOME'" />
        <AboutMeComponent v-if="activeTab === 'ABOUT ME'" />
      </div>
    </div>
  </div>
</template>


<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
import NavigationComponent from "@/components/NavigationComponent.vue";
import HomeComponent from "@/components/HomeComponent.vue";
import AboutMeComponent from "@/components/AboutMeComponent.vue";

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent
  },
  data() {
    return {
      loggedIn: false,
      activeTab: "HOME"
    };
  },
  methods: {
    updateLoginStatus(status) {
      this.loggedIn = status;
    },
    updateActiveTab(tab) {
      this.activeTab = tab;
    }
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #16021D;
}

.content-container {
  display: flex;
}

.nav-container {
  flex: 1;
  color: white;
  padding: 10px;
}

/* Navigation styles */
.navigation {
  color: white;
  padding: 60px 70px;
  width: 100%;
  text-align: center;
}

.navigation button {
  background: transparent;
  border: none;
  color: white;
  cursor: pointer;
}

.navigation button:hover {
  text-decoration: underline;
}

/* Main content styles */
.main-container {
  flex: 4;
  flex-basis: 75%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-top: 20px;
  margin-left: 40px;
}

/* Additional styling for navigation */
.loggedIn-content {
  background-color: '#7E58D0';
}
</style>