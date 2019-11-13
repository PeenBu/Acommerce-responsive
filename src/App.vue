<template>
<div>
  <p style="padding-left:5%; padding-top:2%;">
    Items 1 - {{Id.length}} of {{Id.length}}
    </p>
  <v-app style="padding:2% 5% 2% 5%; backgroundColor:white;">
    <hr style="border: 1px solid rgb(216,216,216)	;">
    <v-row
      class="mb-6"
      no-gutters
    >
      <v-col
        v-for="info in Id" :key="info.id" class="informaiton"
        cols="12"
        xs="12"
        sm="3"
        lg="3"
        md="3"
        xl="3"
      >
        <!-- This is where to put card in  -->
    <v-card
    :loading="loading"
    height="550"
    flat="true" 
    hover="true"
    style="margin-right:3px; margin-bottom:3px" >
    <v-flex style="padding:5%; ;">
      <div>
          <v-img
            height="250"
            :src="info.image_url"
          ></v-img>
          <p style="font-size: 17px;">{{info.title}}</p>
          <p style="font-size: 14px;">{{
            today.diff(moment(info.created_at), 'weeks') == 1 ? `${today.diff(moment(info.created_at), 'week')} week`
            : `${today.diff(moment(info.created_at), 'week')} weeks`
            }} ago</p>
          <v-card-text>
            <v-row
              align="left"
              
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
            
         </v-card-text>
         <p style="text-align: left;font-size: 19px">&#3647;
              {{info.price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")}}.00
            </p>
      </div>
    </v-flex>
  </v-card>
      </v-col>
    </v-row>
    
     <div class="text-center">
    <v-pagination
      v-model="page"
      :length="4"
      prev-icon="mdi-menu-left"
      next-icon="mdi-menu-right"
    ></v-pagination>
  </div>
  <hr style="border: 1px solid rgb(216,216,216)	; margin-top:1%">
  </v-app>
</div>
</template>


<script>
import data from "./assets/list.json";
var moment = require('moment');
export default {
  name: 'app',
  components: {
    
  },

  data: () => ({
     Id : data,
     page: 1,
     moment: moment,
     today : moment(),
  }),
};
</script>
