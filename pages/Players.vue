<template>
  <div class="playerData">
    <playerNav />
    <nuxt-child />
  </div>
</template>

<script>
import playerNav from "@/components/AppHeaderPlayers";
export default {
  components: {
    playerNav
  },
};
</script>

<style lang="scss">
.playerData {
  padding: 50px 0;
}
</style>
