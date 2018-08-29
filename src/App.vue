<template>
  <div>
    <headerBlock
      :userLoggedIn='userLoggedIn'
      :userName='userName'
      :onLogin='onLogin'
    />
  </div>
</template>

<script>
import headerBlock from "./HeaderBlock.vue";

export default {
  data() {
    return {
      userLoggedIn: false,
      userName: ""
    };
  },
  methods: {
    onLogin: function(data) {
      if (data) {
        this.userName = data.userName;
        this.userLoggedIn = !this.userLoggedIn;
      }
    }
  },
  components: {
    headerBlock
  }
};
</script>