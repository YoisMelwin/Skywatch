<template>
  <nav class="navbar">
    <ul>
      <li v-for="(link, index) in links" :key="index">
        <a :href="link.url">{{ link.text }}</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      links: [
        { text: 'Home', url: '/' },
        { text: 'About', url: '/about' }
      ]
    }
  }
}
</script>

<style>
.navbar {
  background-color: #333;
  color: #fff;
  padding: 1.5rem;
}

.navbar ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.navbar ul li {
  display: inline;
  margin-right: 1rem;
}

.navbar ul li a {
  color: #fff;
  text-decoration: none;
}
</style>
