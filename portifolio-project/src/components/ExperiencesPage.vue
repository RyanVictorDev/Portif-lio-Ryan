<template>
  <v-container>
    <p class="title mx-auto text-center mb-12">Experiências</p>

    <v-row>
      <v-col class="d-flex flex-column justify-start border-e-lg" cols="3">
        <v-btn
          v-for="(item, index) in menuItems"
          :key="index"
          class="menu-item"
          :class="{ 'active': selectedButton === item }"
          variant="text"
          align="start"
          @click="selectedButton = item"
        >
          {{ item }}
        </v-btn>
      </v-col>

      <v-col class="d-flex flex-column">
        <v-card class="overflow-auto bg-black" height="200">
          <div class="d-flex justify-between align-center">
            <v-card-title>{{ cards[selectedButton]?.title }}</v-card-title>
            <v-card-subtitle class="ml-auto">{{ cards[selectedButton]?.subtitle }}</v-card-subtitle>
          </div>
          <v-card-title class="text-purple-lighten-1">{{ cards[selectedButton]?.company }}</v-card-title>
          <v-card-text class="text-grey-lighten-1">
            <p>{{ cards[selectedButton]?.description }}</p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const cards = {
  "WDA Tecnologia e Inovação": {
    title: "Estagiário em Desenvolvimento de Full Stack",
    subtitle: "Ago 2024 - Presente",
    company: "WDA Group",
    description: "Desenvolvimento de aplicações web com Vue.js, Quasar, Java e Spring Boot."
  },
  "Experiências": {
    title: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
    subtitle: "Ago 1890 - 2023",
    company: "Alguma outra empresa",
    description: "Desenvolvimento de aplicações web com Vue.js, Quasar, Java e Spring Boot."
  }
} as const;

const menuItems = Object.keys(cards) as (keyof typeof cards)[];

const selectedButton = ref<keyof typeof cards>(menuItems[0]);
</script>

<style scoped>

.menu-item {
  justify-content: flex-start;
  text-align: left;
  transition: all 0.5s;
}

.menu-item.active {
  color: #AB47BC !important;
  font-weight: bold;
}
</style>
