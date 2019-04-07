<template>
  <q-page padding>
    <q-field
      icon='account_circle'
      label='Email'
      :error='mailHasError'
      error-label='We need a valid email'
    >
      <q-input type='email' v-model='email'/>
    </q-field>

    <q-field icon='fingerprint' label='Password'>
      <q-input type='password' v-model='email'/>
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
