<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Poster shop
        </q-toolbar-title>

        <div>Version du site : {{version}}</div>
      </q-toolbar>
    </q-header>

    <q-footer elevated>
        <q-toolbar>
          <div>© 2021 - Poster shop</div>
        </q-toolbar>
      </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Liens importants
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { version } from '../../package.json'
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/projet-scrum',
    icon: 'code',
    link: 'https://github.com/Legoota/Projet-scrum'
  },
  {
    title: 'Trello',
    caption: 'trello.com/projet-scrum',
    icon: 'chat',
    link: 'https://trello.com/b/uzni5nVf/projet-scrum'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData,
      version: version
    }
  }
}
</script>
