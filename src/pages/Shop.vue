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

        <q-card-actions align="right">
          <q-btn v-close-popup flat color="primary" label="Ajouter au panier" />
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
export default {
  name: 'PageShop',
  data () {
    return {
      card: false,
      selected: {},
      catalog: catalog
    }
  },
  methods: {
    selectChange (nom) {
      this.selected = catalog.filter(p => p.title === nom)[0]
      this.card = true
    }
  }
}
</script>
