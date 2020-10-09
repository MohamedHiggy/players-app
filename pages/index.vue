<template>
  <div class="Login">
    <div class="container">
      <form class="Admin-login" @submit.prevent="setData">
        <h1 class="title">Admin Login</h1>

        <!--Admin Email-->
        <div class="form-group">
          <label for="inputemail">Email</label>
          <input
            type="text"
            class="form-control input-focus"
            placeholder="Enter your email"
            id="inputemail"
            name="admin-email"
            v-model="adminemail"
          />
        </div>

        <!--Admin password-->
        <div class="form-group">
          <label for="inputpassword">Password</label>
          <input
            type="password"
            class="form-control input-focus"
            placeholder="Enter your password"
            id="inputpassword"
            name="admin-password"
            v-model="adminpassword"
          />
        </div>

        <button type="submit" class="btn btn-block btn-send">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  components: {},
  data() {
    return {
      adminemail: "",
      adminpassword: "",
    };
  },
  methods: {
    setData: function () {
      const adminLogin = {
        admin_email: this.adminemail,
        admin_password: this.adminpassword,
      };
      const adminLoginDatajson = JSON.stringify(adminLogin);
      console.log(adminLoginDatajson);
    },
  },

};
</script>

<style lang="scss" scoped>
.Login {
  padding: 50px;
  .Admin-login {
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
