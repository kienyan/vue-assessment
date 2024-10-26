<template>
  <div class="container">
    <header class="header">
      <h1>Header</h1>
    </header>
    <div class="main-content">
      <div class="content">
        <p>Content</p>
      </div>
      <div class="sidebar">
        <p>Sidebar</p>
      </div>
    </div>
    <footer class="footer">
      <p>Sticky Footer</p>
    </footer>
  </div>
</template>

<style lang="css" scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: #f3f9f2;
  background-image: linear-gradient(to bottom right, transparent 50%, #3976fe 0),
    linear-gradient(to top right, #3976fe 0%, transparent 0);
  background-size: 50% 100%;
  background-repeat: no-repeat;
  background-position: right, left;
}

.header {
  background-color: #e2ece2;
  color: #000000;
  margin-bottom: 1rem;
  text-align: center;
}

.main-content {
  display: flex;
  flex: 1;
}

.content {
  display: flex;
  flex: 2;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #e2ece2;
  color: #000000;
  margin: 1rem;
}

.sidebar {
  display: flex;
  flex: 1;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #e2ece2;
  color: #000000;
  margin: 1rem;
}

.footer {
  background-color: #e2ece2;
  color: #000000;
  margin-top: 1rem;
  text-align: center;
  position: sticky;
  bottom: 0;
}

@media (max-width: 768px) {
  .main-content {
    flex-direction: column;
  }
}
</style>
