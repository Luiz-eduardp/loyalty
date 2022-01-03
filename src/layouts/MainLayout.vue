<template>
  <q-layout view="lHh Lpr lFf" >
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Nome do restaurante
        </q-toolbar-title>

        <div> v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
       <q-card dark bordered class="bg-grey-9 my-card">
      <q-card-section>
        <div class="text-h6">Loyalty Sys</div>
       
      </q-card-section>

      <q-separator dark inset />

      <q-card-section>
        Contate o Dev para mais funções
      </q-card-section>
    </q-card>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>



import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
  
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
     
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
