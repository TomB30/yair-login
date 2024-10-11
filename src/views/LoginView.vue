<template>
  <div v-if="loading">loading...</div>
  <section v-else class="login-view">
    <div class="login-wrapper">
      <div class="title">Yair amar</div>
      <input type="text" v-model="username" placeholder="username" />
      <input type="password" v-model="password" placeholder="password" />
      <button @click="login">Login</button>

      <span class="create-user"
        >or <span class="link">create a new user</span></span
      >
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'login-view',
  components: {},
  emits: {},
  props: {},
  data() {
    return {
      username: '',
      password: '',
      loading: false,
    }
  },
  async created() {
    this.loading = true
    await this.fetchData()
    this.loading = false
  },
  computed: {},
  methods: {
    login() {
      console.log('this.username =========>', this.username)
      console.log('this.password =========>', this.password)
    },
    async fetchData() {
      return new Promise(resolve => {
        setTimeout(() => {
          resolve('fetchData')
        }, 1000)
      })
    },
  },
})
</script>

<style lang="scss" scoped>
.login-view {
  .login-wrapper {
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin: auto;
    display: flex;
    width: fit-content;
    border-radius: 6px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    flex-direction: column;
    align-items: center;
    gap: 10px;
    padding: 16px;

    .title {
      font-size: 24px;
      font-weight: bold;
      margin-bottom: 8px;
    }

    input {
      border-radius: 6px;
      font-size: 17px;
      padding: 14px 16px;
      width: 330px;
      outline: none;
      border: 1px solid lightgray;
    }

    button {
      background-color: #1877f2;
      border: none;
      border-radius: 6px;
      font-size: 20px;
      line-height: 48px;
      padding: 0 16px;
      width: 330px;
      color: white;
      cursor: pointer;
      transition:
        filter 0.3s,
        transform 3s;

      &:hover {
        filter: brightness(1.1);
        transform: rotate(3600deg);
      }

      &:active {
        filter: brightness(0.9);
      }
    }

    .create-user {
      margin: 24px 0 8px;
      color: gray;

      .link {
        color: #408aeb;
        cursor: pointer;
        transition: filter 0.3s;

        &:hover {
          text-decoration: underline;
        }

        &:active {
          filter: brightness(0.9);
        }
      }
    }
  }
}
</style>
