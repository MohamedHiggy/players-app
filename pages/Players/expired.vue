<template>
  <div class="container-fluid">
    <table class="table mt-5">
      <thead>
        <tr>
          <th scope="col">player Img</th>
          <th scope="col">player Name</th>
          <th scope="col">player address</th>
          <th scope="col">player number</th>
          <th scope="col">player membership</th>
          <th scope="col">player Birth</th>
          <th scope="col">player subscriptions</th>
          <th scope="col">player Date</th>
          <th scope="col">added by</th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <playerData
          v-for="(JsonPlayersData, index) in JsonPlayerData"
          :key="index"
          :player_img="JsonPlayersData.player_img"
          :player_name="JsonPlayersData.player_name"
          :player_address="JsonPlayersData.player_address"
          :player_number="JsonPlayersData.player_number"
          :player_membership="JsonPlayersData.player_membership"
          :player_birth="JsonPlayersData.player_birth"
          :player_subscriptions="JsonPlayersData.player_subscriptions"
          :player_Date="JsonPlayersData.player_Date"
          :Admin_name="JsonPlayersData.Admin_name"
        />
      </tbody>
    </table>
  </div>
</template>
<script>
import playerData from "@/components/PlayerData";
import JsonPlayerData from "@/JSON/player-data";
export default {
  components: {
    playerData
  },
  data() {
    return {
      JsonPlayerData: JsonPlayerData
    };
  }
};
</script>

<style lang="scss">
.filters {
  padding: 0 50px 50px;
  .subscriptions-filter {
    label {
      line-height: 6em;
      cursor: pointer;
      margin: 0 15px;
    }
  }
}
.title {
  text-align: center;
  color: #666666;
  padding: 0 0 50px 0;
}
.table {
  tbody {
    tr {
      .btns {
        button {
          height: 38px;
          margin: 0 15px;
          color: #ffffff;
          &:focus {
            box-shadow: none;
            outline: none;
          }
        }
      }
    }
  }
}
</style>
