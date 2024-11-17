<template>
  <div class="main1">
    <nav>
      <ul class="navbar">
        <li><router-link to="/BookPage" >Book Page</router-link></li>
        <li><router-link to="/AboutPage">About</router-link></li>
        <li><router-link to="/ContactPage">Contact</router-link></li>
        <li>
          <input
            type="text"
            v-model="searchQuery"
            @input="onSearch"
            placeholder="Search for books..."
            class="search-bar"
          />
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'AppNavbar',
  data() {
    return {
      searchQuery: '',
      searchTimeout: null // For debounce
    };
  },
  methods: {
    onSearch() {
      clearTimeout(this.searchTimeout);
      this.searchTimeout = setTimeout(() => {
        this.$emit('search', this.searchQuery);
      }, 300); // Debounce time
    }
  }
};
</script>

<style scoped>
.search-bar {
  margin-left: 20px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.main1 {
  background-color: #2c3e50;
  height: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.navbar {
  list-style: none;
  display: flex;
  justify-content: center;
  padding: 0;
  margin: 0;
}

.navbar li {
  margin: 0 20px;
}

.navbar a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

.navbar a:hover {
  text-decoration: underline;
}
</style>
