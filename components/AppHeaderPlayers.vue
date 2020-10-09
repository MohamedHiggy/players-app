<template>
  <div class="players-nav">
    <ul class="list-style">
      <li class="list">
        <nuxt-link to="/players">All players</nuxt-link>
      </li>
      <li class="list">
        <nuxt-link to="/players/expired">expired players</nuxt-link>
      </li>
    </ul>
  </div>
</template>
<style lang="scss" scoped>
.players-nav {
  .list-style {
    padding: 0;
    list-style: none;
    width: 400px;
    margin: 0 auto;
    display: flex;
    justify-content: space-around;

    .list a {
      color: #666666;
      font-size: 18px;
      padding: 4px 10px;
      border-radius: 3px;
      text-decoration: none;
      font-weight: bold;
    }

    .list a.nuxt-link-exact-active {
      border: 1px solid #666666;
      color: #666666;
    }
  }
}
</style>
