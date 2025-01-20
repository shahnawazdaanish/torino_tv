<template>
  <v-container fill-height class="tv_selection">
    <v-layout fill-height>
      <v-row align="center"
             justify="center">
        <v-col>
          <v-row style="height:100vh;">
            <v-col
              v-for="(page, i) in pages"
              :key="i"
              cols="12"
              md="4"
              class="my-auto"
            >
              <v-card
                :variant="'flat'"
                class="mx-auto text-center"
                color="tonal"
              >
                <v-card-title class="tv_title">{{ 'TV' + (i + 1) }}</v-card-title>
                <v-card-subtitle style="font-size: 50px">Select below button to set</v-card-subtitle>
                <template v-slot:actions>
                  <v-btn
                    :to="page"
                    size="x-large"
                    variant="tonal"
                    class="font-weight-bold tv_selection_button"
                    block text="Play on TV">

                  </v-btn>
                </template>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-layout>
  </v-container>
</template>

<script lang="ts" setup>
//
import RestaurantMenu from "@/components/RestaurantMenu.vue";
</script>

<script lang="ts">
export default {
  data: () => ({
    pages: ['menu1', 'flat', 'flat'],
  }),
}
</script>

<style scoped>
.tv_selection {
  font-family: "Comfortaa", serif;
}
.tv_title {
  font-weight: bold;
  font-size: 120px;
  color: #ffdd75;;
}
.tv_selection_button {
  font-size: 60px;
  padding: 50px 15px;
  color: #c0be10;
}
</style>
