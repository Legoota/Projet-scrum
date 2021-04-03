<template>
  <q-page>
    <div class="row">
      <div class="col"></div>
      <div class="col-10">
        <div class="q-pa-md row items-start q-gutter-md">
          <q-card class="my-card" v-for="poster in catalog" :key="poster.title">
            <q-img :src="poster.lien">
              <div class="absolute-bottom">
                <div class="text-h6">{{poster.title}}</div>
                <div class="text-subtitle2">{{poster.prix}}€</div>
              </div>
            </q-img>

            <q-card-actions>
              <q-btn flat @click="selectChange(poster.title)">Voir plus</q-btn>
              <q-btn flat round color="primary" icon="share" />
            </q-card-actions>
          </q-card>
        </div>
      </div>
      <div class="col"></div>
    </div>
    <q-dialog v-model="card">
      <q-card class="my-card">
        <q-img :src="selected.lien" />

        <q-card-section>

          <div class="row no-wrap items-center">
            <div class="col text-h6 ellipsis">
              {{selected.title}}
            </div>
          </div>

          <q-rating v-model="selected.rating" :max="5" size="32px" />
        </q-card-section>

        <q-card-section class="q-pt-none">
          <div class="text-subtitle1">
            {{selected.description}}
          </div>
        </q-card-section>

        <q-separator />
        <br/>
        <div class="row">
          <div class="col-1"></div>
          <div class="col">
            <q-select
              filled
              v-model="selectedType"
              :options="type"
              label="Choisir"
            />
          </div>
          <div class="col-1"></div>
        </div>
        <br/>
        <q-separator />

        <q-card-actions align="left">
          <span v-if="selectedType === 'Poster'">Prix total : {{selected.prix}}€</span>
          <span v-else-if="selectedType === 'Tableau'">Prix total : {{selected.prix*1.5}}€</span>
          <span v-else>Choisissez une finition pour calculer le prix</span>
        </q-card-actions>

        <q-card-actions align="right">
          <q-btn :disable="selectedType" @click="sendMessage" v-close-popup flat color="primary" label="Ajouter au panier" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<style scoped>
  .my-card {
    margin-left: 5em;
    margin-right: 5em;
  }
</style>

<script>
import { catalog } from '../assets/catalog'
const types = ['Poster', 'Tableau']
export default {
  name: 'PageShop',
  data () {
    return {
      card: false,
      selected: {},
      catalog: catalog,
      type: types,
      selectedType: ''
    }
  },
  mounted () {
    this.prixMax = Math.max.apply(Math, this.catalog.map(function (o) { return o.prix }))
    this.max = this.prixMax
  },
  methods: {
    selectChange (nom) {
      this.selected = catalog.filter(p => p.title === nom)[0]
      this.selectedType = ''
      this.card = true
    },
    sendMessage () {
      this.$q.notify({
        message: 'Article ajouté au panier !',
        color: 'positive'
      })
    }
  }
}
</script>
