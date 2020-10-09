<template>
  <div class="container-fluid">
      <div class="filters">
        <div class="form-row">
          <!--search filter-->
          <div class="form-group col-lg-6">
            <label for="inputsearh">search filter</label>
            <input
              type="search"
              class="form-control input-focus"
              placeholder="search for player"
              id="inputsearh"
              v-model="keyword"
            />
          </div>
          <!--subscriptions filter-->
          <div class="form-group col-lg-6 subscriptions-filter">
            <label>
              <input type="radio" v-model="selectedsubscriptions" value="All" />
              All
            </label>
            <label>
              <input
                type="radio"
                v-model="selectedsubscriptions"
                value="yearly"
              />
              yearly
            </label>

            <label>
              <input
                type="radio"
                v-model="selectedsubscriptions"
                value="Half-yearly"
              />
              Half-yearly
            </label>

            <label>
              <input
                type="radio"
                v-model="selectedsubscriptions"
                value="Quarterly-yearly"
              />
              Quarterly-yearly
            </label>

            <label>
              <input
                type="radio"
                v-model="selectedsubscriptions"
                value="Monthly"
              />
              Monthly
            </label>
          </div>
        </div>
      </div>
      <table class="table">
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
            v-for="(JsonPlayersData, index) in filteredsubscriptions"
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
    playerData,
  },
  data() {
    return {
      JsonPlayerData: JsonPlayerData,
      keyword: "",
      selectedsubscriptions: "All"
    };
  },
  computed: {
    filteredsubscriptions: function() {
      var vm = this;
      var player_subscriptions = vm.selectedsubscriptions;

      if (player_subscriptions === "All") {
        return vm.JsonPlayerData;
      } else {
        return vm.JsonPlayerData.filter(function(JsonPlayerData) {
          return JsonPlayerData.player_subscriptions === player_subscriptions;
        });
      }
    }
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
