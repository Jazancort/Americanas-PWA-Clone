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
      <div>
        <q-btn
          class="full-width q-pl-md q-pb-xs q-pr-md"
          style="font-size: 12px"
          flat
          dense
          no-caps
          align="between"
          icon="fas fa-map-marker-alt"
          icon-right="fas fa-caret-down"
          label="Rua dezessete, Águas Lindas. Ananindeua - PA"
          @click="visible = true"
        >
        </q-btn>
        <q-dialog
          persistent
          position="bottom"
          v-model="visible"
        >
          <q-card
            class="full-height"
            style="">
            <div align="center"><q-btn color="grey-6" icon="far fa-window-minimize" flat v-close-popup /> </div>
            <q-card-section>
              <div class="row">
                <div class="text-black text-h6" style="font-size: 18px"><b>Escolha um endereço</b></div>
                <div
                  class="text-grey-7"
                  style="font-size: 13px; font-weight: 500; "
                >
                  Pra gente te mostrar as melhores ofertas e condições de frete para a sua região :)
                </div>
                <div class="q-pt-sm">
                  <p class="q-pr-xl" style="float:left; font-weight: 500;">Escolha um endereço</p>
                  <p class="q-pl-xl q-ml-xl text-red" style="float:right; font-weight: 500;">adicionar</p>
                </div>
              </div>
              <q-item tag="label" v-ripple>
                <q-item-section avatar>
                  <q-radio v-model="option" val="primeiro" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Julio Leite</q-item-label>
                  <q-item-label caption>Rua dezessete, 5 </q-item-label>
                </q-item-section>
              </q-item>
              <q-separator
                inset="item"
              />
              <q-item tag="label" v-ripple>
                <q-item-section avatar>
                  <q-radio v-model="option" val="segundo" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>Julyete Azancort</q-item-label>
                  <q-item-label caption>Rua A17; Quadra 58, 14</q-item-label>
                </q-item-section>
              </q-item>
            </q-card-section>
             <q-separator color="grey-11" size="7px" />
          </q-card>
          <q-card>
          <q-card-section style="height:70px">
            <q-item>
              <q-item-section avatar>
                <q-icon class="q-pl-sm" style="font-size: 1.4em" name="fas fa-crosshairs" />
              </q-item-section>
              <q-item-section style="font-size:13px">
                <q-item-label>Use sua localização</q-item-label>
              </q-item-section>
            </q-item>
          </q-card-section>

            <q-separator />

          <q-card-section style="height:70px">
            <q-item>
              <q-item-section avatar>
                <q-icon class="q-pl-sm" style="font-size: 1.4em" name="fas fa-search" />
              </q-item-section>
              <q-item-section style="font-size:13px">
                <q-item-label>Use sua localização</q-item-label>
              </q-item-section>
              <q-item-section avatar>
                <q-icon class="q-pl-sm" style="font-size: 1.4em" name="fas fa-chevron-right" />
              </q-item-section>
            </q-item>
          </q-card-section>

          </q-card>
        </q-dialog>
      </div>
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
      visible: false,
      option: '',
      EnderecoDialog: false,
      leftDrawerOpen: false,
      essentialLinks: linksData,
      secondLinks: newLinksData,
      thirdLinks: sellPoint,
      text: '',
      dialogLogin: false,
      isPwd: true,
      isPwdConfirm: true,
      form: {
        nome: '',
        email: '',
        senha: '',
        confirmSenha: ''
      }
    }
  },
  methods: {
    register () {
      this.EnderecoDialog = true
    },
    closeRegister () {
      this.$emit('close')
    }
  }
}
</script>
