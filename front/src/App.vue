<template>
  <v-app>
    <!-- Barra de Aplicação -->
    <v-app-bar app color="indigo" dark>
      <v-toolbar-title>BBox</v-toolbar-title>
      <v-spacer></v-spacer>

      <!-- Botões de navegação (visíveis apenas em telas maiores) -->
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text to="#minha-caixa">Minha Caixa</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text to="#usuario">Usuário</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text to="#pontos-descarte">Pontos de Descarte</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text to="#ranking">Ranking</v-btn>
      
      <v-btn icon v-show="$vuetify.breakpoint.smAndDown" @click="drawer = !drawer">
  <v-icon class="white--text">mdi-menu</v-icon>
    </v-btn>

    </v-app-bar>

    <!-- Drawer (Menu Lateral) para Dispositivos Móveis -->
    <v-navigation-drawer v-model="drawer" temporary app>
      <v-list>
        <v-list-item @click="navigate('#minha-caixa')">
          <v-list-item-title>Minha Caixa</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('#usuario')">
          <v-list-item-title>Usuário</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('#pontos-descarte')">
          <v-list-item-title>Pontos de Descarte</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('#ranking')">
          <v-list-item-title>Ranking</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- Conteúdo Principal -->
    <v-main>
      <div class="container">
        <GoogleMap />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import GoogleMap from './components/GoogleMap.vue';

export default {
  name: 'App',
  components: {
    GoogleMap,
  },
  data() {
    return {
      drawer: false, // Controla a visibilidade do drawer
    };
  },
  methods: {
    navigate(anchor) {
      this.drawer = false; // Fecha o drawer
      window.location.hash = anchor; // Navega para o ID correspondente
    },
  },
};
</script>

<style scoped>
.container {
  padding: 20px;
}
</style>
