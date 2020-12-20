<template>
  <div>
    <!--  用户头像框部分  -->
    <div class="flex flex-center column q-mt-lg">
      <q-avatar class="justify-center" size="100px">
        <img :src="avatarUrl">
      </q-avatar>
      <q-item clickable class="q-mt-md text-h6" @click="loginJump">{{userName}}</q-item>
    </div>

    <q-item clickable tag="a" target="_blank" href="https://quasar.dev">
      <q-item-section avatar>
        <q-icon name="school"/>
      </q-item-section>
      <q-item-section>
        <q-item-label>Docs</q-item-label>
        <q-item-label caption>quasar.dev</q-item-label>
      </q-item-section>
    </q-item>
    <q-item clickable tag="a" target="_blank" href="https://github.com/quasarframework/">
      <q-item-section avatar>
        <q-icon name="code"/>
      </q-item-section>
      <q-item-section>
        <q-item-label>Github</q-item-label>
        <q-item-label caption>github.com/quasarframework</q-item-label>
      </q-item-section>
    </q-item>
    <q-item clickable tag="a" target="_blank" href="https://chat.quasar.dev">
      <q-item-section avatar>
        <q-icon name="chat" />
      </q-item-section>
      <q-item-section>
        <q-item-label>Discord Chat Channel</q-item-label>
        <q-item-label caption>chat.quasar.dev</q-item-label>
      </q-item-section>
    </q-item>
    <q-item clickable tag="a" target="_blank" href="https://forum.quasar.dev">
      <q-item-section avatar>
        <q-icon name="forum" />
      </q-item-section>
      <q-item-section>
        <q-item-label>Forum</q-item-label>
        <q-item-label caption>forum.quasar.dev</q-item-label>
      </q-item-section>
    </q-item>
    <q-item clickable tag="a" target="_blank" href="https://twitter.com/quasarframework">
      <q-item-section avatar>
        <q-icon name="rss_feed" />
      </q-item-section>
      <q-item-section>
        <q-item-label>Twitter</q-item-label>
        <q-item-label caption>@quasarframework</q-item-label>
      </q-item-section>
    </q-item>
  </div>
</template>

<script>
  export default {
    name: "DrawerContent",
    methods: {
      loginJump() {
        this.$router.push('/login')
      }
    },
    computed: {
      avatarUrl() {
        if (this.$store.state.state.headPortrait === '') {
          return require("@/assets/img/logo.png");
        } else {
          return this.$store.state.state.headPortrait;
        }
      },
      userName() {
        if (this.$store.state.state.userNickName === '') {
          return '立即登录';
        } else {
          return this.$store.state.state.userNickName;
        }
      }
    }
  }
</script>

<style scoped>
  #headPortrait {
    margin-top: inherit;
  }
</style>
