<template>

  <div id="app">
    <nav id="navbar-example2" class="navbar bg-light px-3 mb-3">
      <a class="navbar-brand" href="#">
        <img id="inss" src="./assets/i.png" alt="">
      </a>
      <ul class="nav nav-pills">
        <li class="nav-item">
          <a class="nav-link" href="#scrollspyHeading1">
            <router-link to="/movies">Movie</router-link> 
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#scrollspyHeading2">
            <router-link to="/random">Random</router-link>
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#scrollspyHeading2">
            <router-link to="/watch-list">WatchList</router-link>
          </a>
        </li>
       
      </ul>
    </nav>   

    <nav>
      
      
       
      
    </nav>
    <router-view/>
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

#inss {

  width: 50px;
  height: 50px;

}
</style>
