<template>
  <div>
    <h2 style="text-align: center; color: white;">BBox - Lixeiras Inteligentes</h2>
    <p style="text-align: center; color: white;">
      O BBox é uma lixeira inteligente que usa visão computacional para identificar e cadastrar lixo eletrônico, incentivando a reciclagem e oferecendo benefícios como a Recifecoin.
    </p>
    <gmap-map
      :center="center"
      :zoom="16"
      style="width: 100%; height: 500px; background-color: black;"
    >
      <gmap-marker
        v-for="(marker, index) in markers"
        :key="index"
        :position="marker.position"
        :title="marker.title"
        :clickable="true"
        :draggable="false"
        @click="showDetails(marker)"
      ></gmap-marker>
    </gmap-map>

    <div v-if="selectedMarker" style="background-color: white; padding: 20px; margin-top: 20px;">
      <h3>{{ selectedMarker.title }}</h3>
      <img :src="selectedMarker.image" alt="Material do lixo" style="max-width: 200px; margin-bottom: 15px;" />
      <p><strong>Descrição:</strong> {{ selectedMarker.description }}</p>
      <p><strong>Capacidade Máxima:</strong> {{ selectedMarker.maxCapacity }} kg</p>
      <p><strong>Ocupado:</strong> {{ selectedMarker.occupiedCapacity }} kg</p>
      <p><strong>Material Reciclado:</strong> {{ selectedMarker.recycledMaterial }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      center: { lat: -8.0476, lng: -34.8770 }, // Centro de Recife
      markers: [
        {
          position: { lat: -8.0475, lng: -34.8769 },
          title: "Lixeira 1",
          description: "Lixeira para lixo eletrônico (celulares, baterias, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 50, // kg
          occupiedCapacity: 20, // kg
          recycledMaterial: "Celulares, Baterias, Placas de Circuito"
        },
        {
          position: { lat: -8.0480, lng: -34.8775 },
          title: "Lixeira 2",
          description: "Lixeira para lixo eletrônico (computadores, cabos, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 100, // kg
          occupiedCapacity: 50, // kg
          recycledMaterial: "Computadores, Cabos, Teclados"
        },
        {
          position: { lat: -8.0490, lng: -34.8780 },
          title: "Lixeira 3",
          description: "Lixeira para lixo eletrônico (TVs, monitores, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 80, // kg
          occupiedCapacity: 30, // kg
          recycledMaterial: "TVs, Monitores, Placas de TV"
        },
        {
          position: { lat: -8.0460, lng: -34.8755 },
          title: "Lixeira 4",
          description: "Lixeira para lixo eletrônico (baterias, fones de ouvido, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 40, // kg
          occupiedCapacity: 10, // kg
          recycledMaterial: "Baterias, Fones de Ouvido"
        },
        {
          position: { lat: -8.0500, lng: -34.8790 },
          title: "Lixeira 5",
          description: "Lixeira para lixo eletrônico (impressoras, fontes, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 60, // kg
          occupiedCapacity: 25, // kg
          recycledMaterial: "Impressoras, Fontes de Alimentação"
        },
        {
          position: { lat: -8.0520, lng: -34.8800 },
          title: "Lixeira 6",
          description: "Lixeira para lixo eletrônico (baterias de veículos, dispositivos móveis, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 120, // kg
          occupiedCapacity: 80, // kg
          recycledMaterial: "Baterias de Veículos, Dispositivos Móveis"
        },
        {
          position: { lat: -8.0510, lng: -34.8810 },
          title: "Lixeira 7",
          description: "Lixeira para lixo eletrônico (cabos, adaptadores, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 70, // kg
          occupiedCapacity: 35, // kg
          recycledMaterial: "Cabos, Adaptadores"
        },
        {
          position: { lat: -8.0530, lng: -34.8820 },
          title: "Lixeira 8",
          description: "Lixeira para lixo eletrônico (lâmpadas LED, discos rígidos, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 90, // kg
          occupiedCapacity: 40, // kg
          recycledMaterial: "Lâmpadas LED, Discos Rígidos"
        },
        {
          position: { lat: -8.0540, lng: -34.8830 },
          title: "Lixeira 9",
          description: "Lixeira para lixo eletrônico (placas-mãe, fontes, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 100, // kg
          occupiedCapacity: 60, // kg
          recycledMaterial: "Placas-mãe, Fontes"
        },
        {
          position: { lat: -8.0550, lng: -34.8840 },
          title: "Lixeira 10",
          description: "Lixeira para lixo eletrônico (bocais de lâmpadas, fios, etc.)",
          image: "https://via.placeholder.com/150",
          maxCapacity: 110, // kg
          occupiedCapacity: 55, // kg
          recycledMaterial: "Bocais de Lâmpadas, Fios"
        }
      ],
      selectedMarker: null
    };
  },
  methods: {
    showDetails(marker) {
      this.selectedMarker = marker;
    }
  }
};
</script>

<style scoped>
h2, p {
  color: black;
}
</style>
