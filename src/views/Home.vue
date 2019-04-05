<template>
  <div class="container">
    <h1 class="h1">Work time log</h1>
    <img class="mb-2 img-fluid" src="@/assets/home.jpg" alt="logo" />
    <b-form @submit.prevent="onSubmit" @reset.prevent="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Osobne číslo"
        label-for="input-1"
        description="napr. z prizviska 5 znakov plus prve pismeno z mena + 01 ak si neexistuje niekto z rovnakym zaciatkom"
      >
        <b-form-input
          id="input-1"
          v-model="form.accountName"
          type="number"
          required
          placeholder="Napiš osobne čislo zo zmluvy"
        ></b-form-input>
      </b-form-group>
      <b-form-group
        id="input-group-2"
        label="Heslo"
        label-for="input-2"
        description="heslo rovnake ako prihlasovacie do tvojho PC"
      >
        <b-form-input
          id="input-2"
          v-model="form.pass"
          type="password"
          required
          placeholder="Napiš heslo do PC"
        ></b-form-input>
      </b-form-group>

      <b-button class="mr-2" type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

export default class Home extends Vue {
  form = {
    accountName: '',
    pass: ''
  }
  show = true

  onSubmit() {
    console.log(this.form.accountName, this.form.pass)
  }

  onReset() {
    this.form.accountName = ''
    this.form.pass = ''
    this.show = false

    this.$nextTick(() => {
      this.show = true
    })
  }
}
</script>

