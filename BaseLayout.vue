<template>
    <div class="base-layout">
      <header>
        <nav>
          <p>Home</p>
          <p>{{ username }}</p>
        </nav>
      </header>
  
      <main>
        <slot />
      </main>
  
      <footer>
        <p>&copy; 2023</p>
      </footer>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BaseLayout',
    props: {
      username: {
        type: String,
        default: 'Enzo',
      },
    },
  };
  </script>
  
  <style scoped>
  .base-layout {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
  }
  
  header {
    background-color: #3498db;
    color: #ffffff;
    padding: 10px;
    width: 100%;
  }
  
  nav {
    display: flex;
    justify-content: space-between;
  }
  
  footer {
    margin-top: 20px;
    background-color: #3498db;
    color: #ffffff;
    padding: 10px;
    width: 100%;
  }
  </style>
  