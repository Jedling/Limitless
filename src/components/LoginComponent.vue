<template>
  <section class="login">
    <div class="row mt-4">
      <div class="col-1">
        <router-link to="/">
          <div class="home-btn">
            <i class="fas fa-arrow-circle-left"></i>
          </div>
        </router-link>
      </div>
    </div>

    <!-- Show when logged in -->
    <!-- add <section v-if="loggedIn"> when db is done -->
    <section v-if="loggedIn">
      <div class="row">
        <div class="col">
          <MyAccount />
        </div>
      </div>
    </section>

    <!-- Else this  <div v-else>-->
    <div v-else>
      <div class="row justify-content-center mb-5">
        <div class="col-md-4 col-12">
          <form @submit="submit" class="form-wrapper">
            <div class="form-group text-left">
              <label for="email">E-post</label>
              <input
                v-model="email"
                type="email"
                class="form-control input"
                placeholder
                id="email"
              />

              <label for="password">Lösenord</label>
              <input
                v-model="password"
                type="password"
                class="form-control input"
                placeholder
                id="pwd"
              />
            </div>
            <button disabled type="submit" class="btn btn-primary login-btn">
              <div
                v-if="this.loading"
                class="spinner-border spinner-border-sm"
              />
              <span v-else>Logga in</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import MyAccount from "@/components/MyAccount.vue";
import axios from "axios";

@Component({
  components: {
    MyAccount
  }
})
export default class LoginComponent extends Vue {
  private email: string = "";
  private password: string = "";
  private loading: boolean = false;
  private loggedIn: boolean = false;

  // beforeMount() {
  //   this.$store.dispatch('checkIfLoggedIn');
  // }
  // get loggedIn() {
  //   return this.$store.state.loggedIn;
  // }
  private async submit(e: any) {
    e.preventDefault();
    this.loading = true;
    // const response = await axios({
    //   method: "post",
    //   url: "/api/login",
    //   data: {
    //     email: this.email,
    //     password: this.password
    //   }
    // });
    this.loading = false;
    this.loggedIn = true;
    // this.$store.dispatch("checkIfLoggedIn");
  }
}
</script>
<style scoped lang="scss">
.login {
  .home-btn {
    color: var(--primary);
    font-size: 50px;
  }

  .home-btn:hover {
    color: var(--hover);
  }
  .form-wrapper {
    border-radius: 3px;
    background-color: #f5f5f5;
    .input {
      outline: none;
    }
    .login-btn {
      width: 100%;
      outline: none;
      background-color: var(--primary);
    }
    button {
      cursor: not-allowed;
    }
  }
}
</style>
