<template>
  <div class="addplayer">
    <div class="container">
      <form class="add-players-from" @submit.prevent="setData">
        <h1 class="title">add player</h1>
        <!--playerName-->
        <div class="form-group">
          <label for="inputName">Name</label>
          <input
            type="text"
            class="form-control input-focus"
            placeholder="player name"
            id="inputName"
            name="player-name"
            v-model="playerName"
          />
        </div>

        <!--playeraddress-->
        <div class="form-group">
          <label for="inputaddress">Address</label>
          <input
            type="text"
            class="form-control input-focus"
            placeholder="player address"
            id="inputaddress"
            name="player-address"
            v-model="playeraddress"
          />
        </div>

        <!--playeraddress-->
        <div class="form-group">
          <label for="inputnumber">phone number</label>
          <input
            type="text"
            class="form-control input-focus"
            placeholder="player phone number"
            id="inputnumber"
            name="player-number"
            v-model="playernumber"
          />
        </div>

        <!--playernumber-->
        <div class="form-group">
          <label for="inputnumber">membership number</label>
          <input
            type="text"
            class="form-control input-focus"
            placeholder="player membership number"
            id="inputnumber"
            name="player-membershipnumber"
            v-model="playermembership"
          />
        </div>

        <!--selectedDate-->
        <div class="form-group">
          <label for="inputYearsData">Birth</label>
          <select
            class="form-control input-focus"
            id="inputYearsData"
            name="player-Date"
            v-model="selectedDate"
          >
            <option disabled selected>birth of the player</option>
            <option v-for="(dates, index) in selectedDates" :key="index">
              {{ dates }}
            </option>
          </select>
          <img src="../assets/down-arrow.svg" class="select-arrow" alt="" />
        </div>

        <!--playersubscriptions-->
        <div class="form-group">
          <label for="inputsubscriptions">player subscriptions</label>
          <select
            class="form-control input-focus"
            id="inputsubscriptions"
            name="player-subscriptions"
            v-model="playersubscriptions"
          >
            <option disabled selected>subscriptions of the player</option>
            <option v-for="(subscription, index) in subscriptions" :key="index">
              {{ subscription }}
            </option>
          </select>
          <img src="../assets/down-arrow.svg" class="select-arrow" alt="" />
        </div>

         <!--player from to-->
        <div class="form-group">
          <label for="inputaddress" style="display:block">Expire Date</label>
          <date-picker
            name="player-playerpicker"
            v-model="playerpicker"
            lang="en"
            type="date"
            format="YYYY-MM-DD"
            value-type="format"
            placeholder="expire date"
          >
          </date-picker>
        </div>

        
        <!--playerimg-->
        <div class="form-group">
          <label for="inputimg" class="img-preview-label">click to add player img</label>
          <input
            type="file"
            accept="image/*"
            @change="previewImage"
            class="form-control input-focus img-preview"
            placeholder="player membership number"
            id="inputimg"
            name="player-img"
          />
          <div class="border p-2 mt-3" v-if="preview">
            <p>Preview Here:</p>
            <template>
              <img :src="preview" class="img-fluid" />
              <p class="mb-0">file name: {{ image.name }}</p>
              <p class="mb-0">size: {{ image.size/1024 }}KB</p>
            </template>
          </div>
        </div>

        <button type="submit" class="btn btn-block btn-send">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},


  data() {
    return {
      preview: null,
      image: null,
      playerName: "",
      playeraddress: "",
      playernumber: "",
      playermembership: "",
      selectedDate: "",
      playerpicker: "",
      playersubscriptions: "",
      selectedDates: [
        1998,
        1999,
        2000,
        2001,
        2002,
        2003,
        2004,
        2005,
        2006,
        2007,
        2008,
        2009,
        2010,
        2011,
        2012,
        2013,
        2014,
        2015,
        2016,
        2017,
        2018,
        2019,
        2020,
        2021,
        2022,
        2023,
        2024,
        2025,
        2026,
      ],
      subscriptions: [
        "yearly ",
        "Half-yearly ",
        "Quarterly-yearly ",
        "Monthly ",
      ],
    };
  },
  methods: {
    previewImage: function(event) {
      var input = event.target;
      if (input.files) {
        var reader = new FileReader();
        reader.onload = (e) => {
          this.preview = e.target.result;
        }
        this.image=input.files[0];
        reader.readAsDataURL(input.files[0]);
      }
    },
    setData: function () {
      const playerformData = {
        player_name: this.playerName,
        player_address: this.playeraddress,
        player_number: this.playernumber,
        player_membership: this.playermembership,
        player_birth: this.selectedDate,
        player_subscriptions: this.playersubscriptions,
        player_Date: this.playerpicker,
        player_img: this.preview,
      };
      const playerformDatajson = JSON.stringify(playerformData);
      console.log(playerformDatajson);
    },
  },
};
</script>

<style lang="scss" scoped>
.addplayer {
  padding: 50px;
  .add-players-from {
    padding: 30px 0;
    margin: 0 auto;
    width: 45%;
    .btn-send {
      background-color: #e3f2fd;
      color: #000000;
      font-size: 20px;
      &:focus {
        outline: none;
        box-shadow: none;
      }
    }
    .title {
      text-align: center;
      color: #666666;
    }
    .form-group {
      position: relative;
      .img-preview-label {
        width: 100%;
        padding: 5px 0;
        text-align: center;
        background-color: #e3f2fd;
        color: #000000;
        font-size: 20px;
        cursor: pointer;
      }
      .img-preview {
        display: none;
      }
      .mx-datepicker {
        width: 100%;
        .mx-input {
          border-radius: 0;
          cursor: pointer;
          &:hover {
            border-color: #e3f2fd;
          }
          &:focus {
            border-color: #e3f2fd;
            box-shadow: none;
          }
        }
      }
      select {
        cursor: pointer;
        -o-appearance: none;
        -ms-appearance: none;
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
      }
      .select-arrow {
        position: absolute;
        top: 45px;
        right: 20px;
      }
    }
    .form-control {
      border-radius: 0;
    }
    .input-focus {
      &:hover {
        border-color: #e3f2fd;
      }
      &:focus {
        border-color: #e3f2fd;
        box-shadow: none;
      }
    }
  }
}
</style>
