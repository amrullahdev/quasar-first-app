<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="leftDrawerOpen = !leftDrawerOpen" />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-lg">
        <div class="text-h3">Todo App</div>
        <div class="text-subtitle1">
          {{formatWaktu}}
        </div>
      </div>
      <q-img src="~assets/gambar.jpg" class="absolute-top header-image"></q-img>
    </q-header>
    <q-drawer v-model="leftDrawerOpen" show-if-above :width="250" :breakpoint="640">
      <q-scroll-area style="height: calc(100% - 195px); margin-top: 195px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item clickable v-ripple  to="/" exact>
            <q-item-section avatar>
              <q-icon name="inbox" />
            </q-item-section>
            <q-item-section>
              Todo
            </q-item-section>
          </q-item>
          <q-item clickable v-ripple to="help" exact>
            <q-item-section avatar >
              <q-icon name="help" />
            </q-item-section>
            <q-item-section>  
              Help
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
      <q-img class="absolute-top " src="~assets/gambar.jpg" style="height: 192px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>
          <div class="text-weight-bold">Fahmi Amrullah</div>
          <div>@amrullahdev</div>
        </div>
      </q-img>
    </q-drawer>
    </q-drawer>
    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>

  </q-layout>
</template>
<script>
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data() {
    return {
      leftDrawerOpen: false,
      formatWaktu: '',
      newTask:'',
      dense: false,
    }
  },
  mounted() {
    this.hariIni()
  },
  methods: {
    hariIni() {
      let waktu = Date.now();
      this.formatWaktu = date.formatDate(waktu, 'd MMM YYYY')
    },
    tambahTask(){

    }
  }
}

</script>
<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.5;
  filter: grayscale(100%)
}

</style>
