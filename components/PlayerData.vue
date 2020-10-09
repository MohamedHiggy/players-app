<template>
  <tr class="playerData">
    <th><img :src="player_img" class="player-avatar"></th>
    <th scope="row">{{ player_name }}</th>
    <td>{{ player_address }}</td>
    <td>{{ player_number }}</td>
    <td>{{ player_membership }}</td>
    <td>{{ player_birth }}</td>
    <td>{{ player_subscriptions }}</td>
    <td>{{ player_Date }}</td>
    <td>{{ Admin_name }}</td>
    <td class="btns">
      <template v-if="this.$route.name  === 'Players-expired'">
        <button class="btn btn-info edit-btn">
          Renew
        </button>
      </template>
      <template v-else>
        <button class="btn btn-primary edit-btn">
          Edit
        </button>
      </template>
      <button class="btn btn-danger delete-btn">
        Delete
      </button>
    </td>
  </tr>
</template>
<script>
export default {
  props: [
    "player_img",
    "player_name",
    "player_address",
    "player_number",
    "player_membership",
    "player_birth",
    "player_subscriptions",
    "player_Date",
    "Admin_name",
  ],
};
</script>

<style lang="scss" scoped>
.player-avatar  {
  width: 50px;
}
</style>
