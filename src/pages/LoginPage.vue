<template>
  <q-page padding>
    <q-field
      icon='account_circle'
      label='Email'
    >
      <q-input type='email' class='q-mt-md' v-model='email'/>
    </q-field>

    <q-field icon='fingerprint' label='Password'>
      <q-input type='password' class='q-mt-md' v-model='password'/>
    </q-field>

    <q-btn color='dark' class="q-mt-xl float-right" @click='login'>Login</q-btn>
  </q-page>
</template>

<script>
export default {
  name: 'PageLogin',
  data() {
    return {
      email: '',
      password: '',
      loading: false,
    };
  },
  methods: {
    login() {},
  },
};
</script>

<style>
</style>
