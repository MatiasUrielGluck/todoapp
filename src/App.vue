<template>
  <div id="app">
    <h1>#todo</h1>
    <nav>
      <router-link to="/">All</router-link>
      <router-link to="/active">Active</router-link>
      <router-link to="/completed">Completed</router-link>
    </nav>
    <transition name="fade">
      <router-view/>
    </transition>
    <!-- <router-view/> -->
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
#app {
  font-family: 'Poppins', sans-serif;
  margin: auto;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 40%;
  height: 100vh;
}

h1 {
  margin-top: 2rem;
}

nav {
  width: 100%;
  margin-top: 3rem;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  padding: 0 2rem;
  align-items: center;
  margin-bottom: 2rem;
  border-bottom: 1px solid rgb(198, 198, 198);
}

nav a {
  text-decoration: none;
  color: black;
  padding: 0.5rem 2rem 1rem;
}

nav a.router-link-exact-active {
  border-bottom: 4px solid blue;
}

.fade-enter-active {
  transition: opacity 2s 0.21s;
}

.fade-leave-active {
  transition: opacity 0.2s;
}

.fade-enter{
  opacity: 0;
}
.fade-leave-to {
  opacity: 0
}

@media only screen and (max-width: 1200px) {
  #app {
    width: 60%;
  }
}

@media only screen and (max-width: 800px) {
  #app {
    width: 80%;
  }
}

@media only screen and (max-width: 500px) {
  #app {
    width: 95%;
  }

  nav {
    padding: 0;
  }
}
</style>
