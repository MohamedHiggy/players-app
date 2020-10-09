<template>
  <nav class="navbar shadow navbar-expand-lg ">
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <nuxt-link to="/addplayer" class="nav-link">Add player</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/players" class="nav-link">Players</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/" class="nav-link">Login</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/register" class="nav-link">Register</nuxt-link>
        </li>
      </ul>
      <form class="form-inline">
          <button class="btn btn-light">logout</button>
       </form>
    </div>
  </nav>
</template>

<style scoped>
.navbar{ 
    background-color: #e3f2fd;
}

.navbar-nav{
    margin: 0 auto;
}

.nav-item {
    margin: 0 10px;
} 
.nav-item a{
    color: #666666;
    font-size: 18px;
    padding: 4px 10px;
    border-radius: 3px;
    border: 1px solid #e3f2fd;
}

.nav-item a.nuxt-link-exact-active{
    font-weight: bold;
}
</style>