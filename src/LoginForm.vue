<template>
    <form action="" class="login-form">
        <div class="login-form-field"
          :class='{error: errorUserName}'
        >
            <label>Name</label>
            <input type="text" v-model='userName'>
        </div>

        <div class="login-form-field"
          :class='{error: errorUserPass}'
        >
            <label>Password</label>
            <input type="password" v-model='userPass'>
        </div>

        <button class="btn" @click.prevent='login()'>Login</button>
    </form>
</template>

<script>
export default {
  props: ["onLogin"],
  data() {
    return {
      userName: "",
      userPass: "",
      errorUserName: false,
      errorUserPass: false
    };
  },
  methods: {
    login: function() {
      let data;

      // in the future there should be correct validation, not this shit! :)
      this.userName
        ? (this.errorUserName = false)
        : (this.errorUserName = true);
      this.userPass
        ? (this.errorUserPass = false)
        : (this.errorUserPass = true);

      if (!this.errorUserName && !this.errorUserPass) {
        let data = {
          userName: this.userName,
          userPass: this.userPass
        };
        this.onLogin(data);
      }
    }
  }
};
</script>


<style>
.login-form {
  display: flex;
}
.login-form-field {
  margin: 0px 10px;
}
.login-form label {
  margin-right: 10px;
  font-weight: 600;
}
</style>

