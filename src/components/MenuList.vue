<template>
  <v-row class="menu_block">
    <v-col
      v-for="(sub_menu, i) in menu"
      :key="i"
      :cols="12"
      :md="6"
      :lg="6"
    >
      <div class="menu-card">
        <v-card variant="text" color="surface-variant" class="menu-card__item">
          <v-card-title>{{ sub_menu.name }}</v-card-title>
          <v-card-subtitle class="menu_subtitle">{{ sub_menu.sub_name }}</v-card-subtitle>
          <v-card-text>

            <v-table class="menu_table" density="compact">
              <thead>
              <tr>
                <th class="border-0"></th>
                <th class="text-left border-0">

                </th>
                <th class="text-center price_column_min" v-if="sub_menu.price_columns === 2">
                  Norm.
                </th>
                <th class="text-center price_column_min" v-if="sub_menu.price_columns === 2">
                  Perhe
                </th>
                <th class="border-0 price_column_min" v-if="sub_menu.price_columns === 1"></th>
              </tr>
              </thead>
              <tbody>
              <tr
                class="menu_table_row"
                v-for="(item, index) in sub_menu.items"
                :key="index"
              >
                <td class="border-0 menu_item_title">{{ item.number }}</td>
                <td class="text-left border-0 menu_item_mw">
                  <v-card-text class="menu_item_title">
                    {{ item.name }}
                  </v-card-text>
                  <v-card-text class="menu_item_subtitle">{{ item.ingredients.join(', ') }}</v-card-text>

                </td>
                <td v-if="item.prices.length === 2" class="border-0 price_column_min menu_item_title">{{ format_price(item.prices[0]) }}</td>
                <td v-if="item.prices.length === 2" class="border-0 price_column_min menu_item_title">{{ format_price(item.prices[1]) }}</td>
                <td v-else class="border-0 price_column_min menu_item_title">{{ format_price(item.prices) }}</td>
              </tr>
              </tbody>
            </v-table>
          </v-card-text>
        </v-card>
      </div>
    </v-col>
  </v-row>

</template>

<script setup lang="ts">
import {defineProps, PropType} from "vue";

defineProps({
  menu: {
    type: Array,
    default: () => [],
    required: true,
  }
});

let format_price = (price) => {
  return Number(price).toLocaleString("es-ES", {minimumFractionDigits: 2});
}
</script>

<style scoped>
.menu_table {
  background: transparent;
}
.menu_table_row {
  margin: 30px 0 !important;
}
.v-card-text {
  padding: 6px 5px;
}

.price_column_min {
  /*min-width: 30px;*/
  font-size: 30px;
}

.menu_subtitle {
  color: #fff;
  font-size: 55px;
  font-weight: bold;
  text-align: left;
  margin-left: 50px;
  opacity: 1;
}

.menu_item_title {
  color: #fddb88;
  font-size: 35px;
}
.menu_item_mw {
  max-width: 310px;
}

.menu_item_subtitle {
  color: #fff;
  font-family: "Comfortaa", serif;
  font-size: 16px;
}
</style>

