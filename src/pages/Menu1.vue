<template>
  <v-container fluid class="fill-height px-16">
    <v-layout fill-height>
      <v-row align="center"
             justify="center">
        <v-col>
          <v-row align="stretch" class="d-flex align-stretch">
            <v-col
              v-for="(menu, i) in menu_prices"
              :key="i"
              :cols="menu.colsize"
              :md="menu.colsize"
            >
              <v-card
                :variant="'text'"
                class="mx-auto text-center fill-height menu_background"
              >
                <v-card-title class="tv_title">{{ menu.name }}</v-card-title>
                <v-card-subtitle></v-card-subtitle>
                <v-card-item class="menu_block">
                  <MenuList :menu="menu.items"></MenuList>
                </v-card-item>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-layout>
  </v-container>
  <BackgroundSlideshow />
</template>


<script lang="ts">
import prices from "@/assets/prices/menu1.json";
import MenuList from "@/components/MenuList.vue";
import BackgroundSlideshow from '@/components/Slideshow.vue';

export default {
  name: "RestaurantMenu1",
  components: {MenuList, BackgroundSlideshow},
  data: function() {
    return {
      menu_prices: prices,
      columns: 2,
    };
  },
};
</script>

<style scoped>
.menu_block {
  box-sizing: border-box;
}
.tv_title {
  font-family: "Lobster", serif;
  color: #f6841e;
  font-size: 120px;
  font-weight: bold;
  text-transform: uppercase;
}
.menu_background {
  background: rgba(17, 17, 17, 0.9);
  padding: 30px 0;
}
</style>
