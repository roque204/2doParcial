<template>
  <div id="app">
    <nav>

      <router-link to="/about">Inicio</router-link>|
      <router-link to="/">Favorito</router-link> 
      
    </nav>
    <router-view/>

    <header>
        <form id="form">
            <input type="text" placeholder="Search" id="search" class="search">
            <input type="number" placeholder="Año" id="year" name="year" class="search">
            <button type="submit" class="search">Buscar</button>
        
          </form>
    </header>

    <main id="main"> </main>

    <footer class="container">

<div class="footer-credits">
    <p class="paragraph text-title">© 2023 Emae.</p>
    <p class="paragraph text-title">Roque Mamani | Pablo Quipildor.</p>
</div>



</footer>

    
  </div>



</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.footer-credits
{
  background-color: white;
}

</style>
