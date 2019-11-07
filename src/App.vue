<template>
  <v-app>
    <v-row
      class="mb-6"
      no-gutters
    >
      <v-col
        v-for="info in Id" :key="info.id" class="informaiton"
        cols = "3"
      >
        <!-- This is where to put card in  -->
    <v-card
    :loading="loading"
    class="mx-1 my-1"
    max-width="350"
    height="550"
    >
    <v-flex>
    <v-img
      height="250"
      :src="info.image_url"
    ></v-img>
     <p>ID: {{info.id}}</p>
    <v-card-title>{{info.title}}</v-card-title>
    <v-card-title>{{info.created_at}}</v-card-title>
    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :value=info.vote
          color="red"
          dense
          half-increments
          readonly
          size="17"
        ></v-rating>

      </v-row>

      <div class="my-4 subtitle-1 black--text">	&#3647;
         {{info.price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")}}
      </div>
    </v-card-text>
    </v-flex>
  </v-card>
      </v-col>
    </v-row>
    <List>
      
    </List>
     <div class="text-center">
    <v-pagination
      v-model="page"
      :length="4"
      prev-icon="mdi-menu-left"
      next-icon="mdi-menu-right"
    ></v-pagination>
  </div>
  </v-app>
  
</template>


<script>
import List from './components/list';
import data from "./assets/list.json";
export default {
  name: 'app',
  components: {
    List,
  },

  data: () => ({
     Id : data,
     page: 1,
  }),
};
</script>
