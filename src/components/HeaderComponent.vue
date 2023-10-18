<template>
  <div class="header" :style="{ backgroundColor: loggedIn ? '#7E58D0' : '#333' }">
    <div class="nav-left">
      <img class="logo" src="@/assets/logo.svg" alt="Logo" />
      <span class="brand">Kraken.fm</span>
    </div>
    <div class="nav-right">
      <span v-if="loggedIn" class="user-info">{{ userFullName }}</span>
      <button @click="toggleLoginStatus" :class="{ 'login-button': !loggedIn, 'logout-button': loggedIn }">
        {{ loggedIn ? 'LOGOUT' : 'LOGIN' }}
      </button>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      user: {
        name: "Ieva Madara",
        surname: "Glavecka",
        code: "IT21043"
      },
      loggedIn: false
    };
  },
  computed: {
    userFullName() {
      return this.loggedIn ? `${this.user.name} ${this.user.surname}` : '';
    }
  },
  methods: {
    toggleLoginStatus() {
      const confirmMessage = this.loggedIn
        ? "Do you want to log out?"
        : "Do you want to log in?";
      if (confirm(confirmMessage)) {
        this.loggedIn = !this.loggedIn;
        this.$emit("loginStatusChanged", this.loggedIn);
      }
    }
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
  padding: 10px 20px;
  border-bottom: 2px solid purple;
}

.nav-left {
  display: flex;
  align-items: center;
}

.logo {
  width: 30px;
  height: 30px;
  margin-right: 10px;
}

.brand {
  font-size: 1.2em;
  font-weight: bold;
}

.nav-right {
  display: flex;
  align-items: center;
}

.login-button,
.logout-button {
  cursor: pointer;
  background-color: transparent;
  border: 1px solid #7E58D0;
  color: white;
  padding: 8px 16px;
  border-radius: 5px;
  margin-left: 10px;
}

.login-button:hover,
.logout-button:hover {
  background-color: #7E58D0;
  border-color: white;
}

.user-info {
  margin-right: 10px;
  border-right: 1px solid white; 
  padding-left: 10px;
  padding-right: 10px;
}
</style>
