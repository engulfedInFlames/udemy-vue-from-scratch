<script setup>
import { computed } from 'vue';
import { useStore } from 'vuex';

const store = useStore();

const isLoggedIn = computed(() => store.getters.isAuthenticated);

const links = {
  coaches: {
    name: 'coaches',
  },
  requests: {
    name: 'requests',
  },
  login: {
    name: 'auth',
  },
};

function logout() {
  store.dispatch('logout');
}
</script>

<template>
  <header>
    <nav>
      <h1>
        <RouterLink :to="links.coaches"> Find a Coach </RouterLink>
      </h1>
      <ul>
        <li>
          <RouterLink :to="links.coaches">All Coaches</RouterLink>
        </li>
        <li v-if="isLoggedIn">
          <RouterLink :to="links.requests">All Requests</RouterLink>
        </li>
        <li v-else>
          <RouterLink :to="links.login">Login</RouterLink>
        </li>
        <li v-if="isLoggedIn">
          <BaseButton @click="logout">Logout</BaseButton>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  height: 5rem;
  background-color: #3d008d;
  display: flex;
  justify-content: center;
  align-items: center;
}

header a {
  text-decoration: none;
  color: #f391e3;
  display: inline-block;
  padding: 0.75rem 1.5rem;
  border: 1px solid transparent;
}

a:active,
a:hover,
a.router-link-active {
  border: 1px solid #f391e3;
}

h1 {
  margin: 0;
}

h1 a {
  color: white;
  margin: 0;
}

h1 a:hover,
h1 a:active,
h1 a.router-link-active {
  border-color: transparent;
}

header nav {
  width: 90%;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

li {
  margin: 0 0.5rem;
}
</style>
