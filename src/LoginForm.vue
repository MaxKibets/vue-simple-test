<template>
    <form action="" class="login-form">
        <input type="text" v-model='userName' :class='{error: errorUserName}' placeholder="Name">
        <input type="password" v-model='userPass' :class='{error: errorUserPass}' placeholder="Password">

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
  flex-wrap: wrap;
}
.login-form input,
.login-form button {
  margin-left: 10px;
}
</style>

