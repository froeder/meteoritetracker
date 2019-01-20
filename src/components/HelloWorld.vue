<template>
  <v-container>
    <v-layout
      text-xs-center
      wrap
    >
      <v-flex>
        <v-card class="texto-nasa">
          <v-card-text>
            A terra constantemente é atingida por rochas espaciais. Aqueles que sobrevivem ao entrar na atmosfera e colidem com a superfície são chamados de meteoritos.
            <br>
            A <strong>nasa</strong>  mantém um regristro histórico de todas essas colições, com informações sobre nome, ano, massa e geolocalização do meteorito.
            <br>
            foi com esses dados que esse site foi construído. para acessar a base de dados, <a href="https://data.nasa.gov/Space-Science/Meteorite-Landings/gh4g-9sfh" target="no_blank">Clique aqui</a>.
          </v-card-text>
        </v-card>
      </v-flex>
    
      <v-flex style="padding-top:40em">
        <v-card>
          <v-card-title style="font-family:Orbitron ; font-weight:600">
          Dados tabulados
          <v-spacer></v-spacer>
          <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        </v-card-title>
        <v-data-table
          :headers="headers"
          :items="meteoritos"
          :search="search"
        >
          <template slot="items" slot-scope="props">
            <td class="text-xs-left">{{ props.item.name }}</td>
            <td class="text-xs-left">{{ props.item.recclass }}</td>
            <td class="text-xs-left">{{ props.item.massa / 1000 }}</td>
            <td class="text-xs-left">{{ props.item.year.split('/')[2].split(' ')[0] }}</td>
          </template>
          <v-alert slot="no-results" :value="true" color="error" icon="warning">
            Sua busca por "{{ search }}" não retornou resultados.
          </v-alert>
        </v-data-table>
        </v-card>
      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>
import meteoros from '../assets/meteoros.json'

  export default {
    data () {
      return {
        search: '',
        headers: [
          { text: 'Cidade', value: 'name' },
          { text: 'Classe' },
          { text: 'Massa (kg)', value:'massa' },
          { text: 'Ano', value: 'year' },
        ],
        meteoritos: meteoros
      }
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Major+Mono+Display|Montserrat+Alternates|Orbitron|Poiret+One|Thasadith');

.texto-nasa{
  font-family: 'Major Mono Display', monospace;
  font-size: 1em ;
  font-weight: bold
}
</style>

