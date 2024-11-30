<script lang="ts">
import { defineComponent } from 'vue';
import DsfrPostale from 'dsfr-postale';

interface Address {
  [key: string]: string | number | undefined;
}

export default defineComponent({
  name: 'App',
  components: {
    DsfrPostale
  },
  data() {
    return {
      adresse: {} as Address
    };
  },
  methods: {
    handleAddressSelected(address: Address): void {
      this.adresse = address;
    }
  }
});
</script>


<template>
  <h1 class="fr-h4">Démonstration du paquet dsfr-postale</h1>
  <div class="fr-container">
    <div class="fr-grid-row">
      <div class="fr-col-lg-12">
        <DsfrPostale label="Votre adresse postale à Poitiers" hint="Saisissez au moins 3 caractères pour obtenir des suggestions" postcode="86000" @addressSelected="handleAddressSelected" />
        <ul class="resultat">
          <li v-for="(value, key) in adresse"> {{ key }} : {{ value }} </li>
        </ul>
      </div>
    </div>
    <a href="https://adresse.data.gouv.fr" class="fr-link">Précisions sur la base de données</a>
  </div>
</template>

<style scoped>
  @import 'https://cdn.jsdelivr.net/npm/@gouvfr/dsfr@1.12.1/dist/dsfr.min.css';
</style>
