<template>
  <q-page>
    <div class="row">
      <div class="col"></div>
      <div class="col-8">
        <h2 class="text-center">Contact</h2>
      </div>
      <div class="col"></div>
    </div>
    <div class="row">
      <div class="col"></div>
      <div class="col-8">
        <div class="q-pa-md">
          <div class="q-gutter-md">
          <q-input outlined v-model="nom" label="Nom" />
          <q-input outlined v-model="prenom" label="Prénom" />
          <q-input outlined v-model="email" type="email" label="Email" />
          <q-input
            v-model="text"
            filled
            type="textarea"/>
          <q-btn :disable="!nom || !prenom || !email || !text" @click="sendMessage" color="primary" icon-right="send" label="Envoyer" />
      </div>
    </div>
      </div>
      <div class="col"></div>
    </div>

  </q-page>
</template>

<script>
export default {
  name: 'PageContact',
  data () {
    return {
      nom: null,
      prenom: null,
      email: null,
      text: null
    }
  },
  methods: {
    sendMessage () {
      this.$q.notify({
        message: 'Message bien envoyé !',
        color: 'positive'
      })
      this.nom = null
      this.prenom = null
      this.email = null
      this.text = null
    }
  }
}
</script>
