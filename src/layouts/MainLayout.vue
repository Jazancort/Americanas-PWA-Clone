<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-red-14">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title class="q-pt-sm">
          <img
            alt="Americanas logo"
            src="AmBranca.png"
            width="115"
          >
        </q-toolbar-title>
        <div>
          <q-input dark borderless v-model="text" style="width:175px" input-class="text-right" class="q-ml-md">
            <template v-slot:append>
              <q-icon v-if="text === ''" color="white" style="font-size: 1.2em;" name="search" />
              <q-icon v-else name="clear" color="white" class="cursor-pointer" @click="text = ''" />
              <q-icon class="q-pl-md q-pb-xs" name="fas fa-shopping-basket" style="font-size: 1.1em;" color="white"></q-icon>
            </template>
          </q-input>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
      :width="250"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8 q-pt-xl"
        >
        <q-header
          style="height:60px"
          class="bg-red-14"
        >
          <div class="row">
            <q-icon class="col-2 q-pl-sm q-pt-sm" name="fas fa-user" style="font-size: 2.4em;" color="white"></q-icon>
            <q-item-section class="q-pt-sm q-pl-md">
              <q-item-label class="q-pt-xs text-white">Julio</q-item-label>
              <q-item-label style="opacity: 0.8;" caption class="text-grey-12" >
                julioazancort@gmail.com
              </q-item-label>
            </q-item-section>
            <q-icon class="col-2 q-pb-lg q-pt-sm" name="fas fa-cog" style="font-size: 1.5em; opacity: 0.6;" color="black"></q-icon>
            <!-- <p class="row col q-pt-md q-pl-sm">Julio</p>
            <p class="col q-pt-md q-pl-sm">julioazancort@gmail.com</p> -->
          </div>
        </q-header>
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
        <q-separator/>
        <second-link
          v-for="link in secondLinks"
          :key="link.title"
          v-bind="link"
        />
        <q-separator/>
        <third-link
          v-for="link in thirdLinks"
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
import EssentialLink from 'components/EssentialLink.vue'
import SecondLink from 'src/components/SecondLink.vue'
import ThirdLink from 'src/components/ThirdLink.vue'

const linksData = [
  {
    title: 'Destaques',
    caption: '',
    icon: 'fas fa-shopping-cart',
    link: ''
  },
  {
    title: 'Departamentos',
    caption: '',
    icon: 'fas fa-list',
    link: ''
  },
  {
    title: 'Favoritos',
    caption: '',
    icon: 'fas fa-heart',
    link: ''
  },
  {
    title: 'Meus Pedidos',
    caption: '',
    icon: 'fas fa-bookmark',
    link: ''
  },
  {
    title: 'Meus Vales',
    caption: '',
    icon: 'fas fa-receipt',
    link: ''
  },
  {
    title: 'Notificações',
    caption: '',
    icon: 'fas fa-bell',
    link: ''
  },
  {
    title: 'Cartão Americanas',
    caption: '',
    icon: 'favorite',
    link: ''
  },
  {
    title: 'Mensagens',
    caption: '',
    icon: 'fas fa-inbox',
    link: ''
  }
]

const newLinksData = [
  {
    title: 'Modo Loja',
    caption: '',
    icon: 'fas fa-store',
    link: ''
  },
  {
    title: 'Ache uma Loja',
    caption: '',
    icon: 'fas fa-map-marker-alt',
    link: ''
  },
  {
    title: 'Aqui tem desconto',
    caption: '',
    icon: 'fas fa-tag',
    link: ''
  },
  {
    title: 'Leitor de código de barras',
    caption: '',
    icon: 'fas fa-barcode',
    link: ''
  }
]
const sellPoint = [
  {
    title: 'Venda com a gente'
  },
  {
    title: 'Atendimento pelo telefone'
  },
  {
    title: 'Compra pelo telefone'
  },
  {
    title: 'Regras de descontos'
  },
  {
    title: 'Regras de compras online'
  },
  {
    title: 'Regras do cupons'
  },
  {
    title: 'Sobre o app'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink, SecondLink, ThirdLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData,
      secondLinks: newLinksData,
      thirdLinks: sellPoint,
      text: ''
    }
  }
}
</script>
