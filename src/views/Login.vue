<template>
  <Login v-bind:childProps="{ onSubmit, routeTo }" />
</template>

<script>
import { LOGIN } from "@/store/actions.type";
import Login from "plutt-vue-login/build/proxy/vue";

export default {
  name: "RwvLogin",
  components: {
    Login
  },
  data() {
    return {
      email: null,
      password: null
    };
  },
  methods: {
    onSubmit(email, password) {
      this.$store
        .dispatch(LOGIN, { email, password })
        .then(() => this.$router.push({ name: "home" }));
    },
    routeTo(name) {
      this.$router.push({ name });
    }
  }
};
</script>
