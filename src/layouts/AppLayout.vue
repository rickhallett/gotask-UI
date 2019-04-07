<template>
  <q-layout view="lHh Lpr lFf">
    <q-layout-header>
      <q-toolbar
        color="dark"
        :glossy="$q.theme === 'mat'"
        :inverted="$q.theme === 'ios'"
      >
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>
          GoTask
          <div slot="subtitle">Running on Quasar v{{ $q.version }}</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-layout-header>

    <q-layout-drawer
      v-model="leftDrawerOpen"
      :content-class="$q.theme === 'mat' ? 'bg-grey-2' : null"
    >
      <q-list
        no-border
        link
        inset-delimiter
      >
        <q-list-header>Navigation</q-list-header>
        <q-item @click.native="$router.push({ path: 'home' })">
          <q-item-side icon="school" />
          <q-item-main label="Home" sublabel="" />
        </q-item>
        <q-item @click.native="$router.push({ path: 'register' })">
          <q-item-side icon="school" />
          <q-item-main label="Register" sublabel="" />
        </q-item>
        <q-item @click.native="$router.push({ path: 'login' })">
          <q-item-side icon="code" />
          <q-item-main label="Login" sublabel="" />
        </q-item>
        <q-item @click.native="$router.push({ path: 'todos' })">
          <q-item-side icon="chat" />
          <q-item-main label="My Todos" sublabel="" />
        </q-item>
        <q-item @click.native="$router.push({ path: 'profile' })">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="My Profile" sublabel="" />
        </q-item>
      </q-list>
    </q-layout-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar';

export default {
  name: 'MyLayout',
  data() {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
    };
  },
  methods: {
    openURL,
  },
};
</script>

<style>
</style>
