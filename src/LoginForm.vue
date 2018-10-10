<template>
    <form action="" class="login-form">
        <input type="text" v-model='userName' :class='{error: hasErrorUserName}' placeholder="Name">
        <input type="password" v-model='userPass' :class='{error: hasErrorUserPass}' placeholder="Password">

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
      hasErrorUserName: false,
      hasErrorUserPass: false
    };
  },
  methods: {
    login: function() {
      let data;

      // in the future there should be correct validation, not this shit! :)
      this.userName
        ? (this.hasErrorUserName = false)
        : (this.hasErrorUserName = true);
      this.userPass
        ? (this.hasErrorUserPass = false)
        : (this.hasErrorUserPass = true);

      if (!this.hasErrorUserName && !this.hasErrorUserPass) {
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

