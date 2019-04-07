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

    <q-field icon='account_circle' label='Username'>
      <q-input type='text' v-model='username'/>
    </q-field>

    <q-field icon='fingerprint' class='q-mt-lg' label='Password'>
      <q-input type='password' v-model='password'/>
    </q-field>

    <q-btn color='dark' class='q-mt-xl float-right' @click='register'>Register</q-btn>
  </q-page>
</template>

<script>
export default {
  name: 'PageRegister',
  data() {
    return {
      email: '',
      username: '',
      password: '',
    };
  },
  methods: {
    register() {},
  },
};
</script>

<style>
</style>
