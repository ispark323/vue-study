<template>
  <div class="auth__form-group">
    <form class="auth__form auth__form--login">
      <input class="auth__input auth__input--email" placeholder="email" type="text" v-model="email" />
      <input
        class="auth__input auth__input--password"
        placeholder="password"
        type="password"
        v-model="password"
        @keypress.enter="handleSubmit"
      />
      <button class="auth__button auth__button--submit" type="submit" @click.prevent="handleSubmit">
        <md-button class="md-icon-button">
          <md-icon>vpn_key</md-icon>
        </md-button>
      </button>
      <button class="auth__return" @click.prevent.stop="onClickReturnFormStatus">
        <md-button class="md-icon-button">
          <md-icon>keyboard_return</md-icon>
        </md-button>
      </button>
    </form>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
export default {
  props: {
    onClickReturnFormStatus: Function,
  },
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    ...mapActions(['logIn']),
    handleSubmit() {
      const loginData = {
        email: this.email,
        password: this.password,
      };
      this.logIn(loginData);
    },
  },
};
</script>
