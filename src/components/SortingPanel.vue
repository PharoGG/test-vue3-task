<template>
  <v-container class="sort-panel" :style="`background: ${options.color}`">
    <v-row align="center" justify="center">
      <v-col cols="auto">
        <v-btn
          variant="tonal"
          color="white"
          icon
          @click="sortAscending"
          :disabled="currentSort === 'asc'"
        >
          <v-icon>mdi-sort-descending</v-icon>
          <v-tooltip activator="parent" location="top">
            По убыванию рейтинга
          </v-tooltip>
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn
          variant="tonal"
          color="white"
          icon="mdi-sort-descending"
          @click="sortDescending"
          :disabled="currentSort === 'desc'"
        >
          <v-icon>mdi-sort-ascending</v-icon>
          <v-tooltip activator="parent" location="top">
            По возрастанию рейтинга
          </v-tooltip>
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn
          variant="tonal"
          color="white"
          icon="mdi-sort"
          @click="withoutSort"
          :disabled="currentSort === 'none'"
        >
          <v-icon>mdi-sort</v-icon>
          <v-tooltip activator="parent" location="top">
            Без сортировки
          </v-tooltip>
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, inject } from "vue";

const currentSort = ref("none");
const props = defineProps({
  options: Object,
});

const emit = defineEmits(["sort"]);

function sortAscending() {
  currentSort.value = "asc";
  emit("sort", "asc");
}

function sortDescending() {
  currentSort.value = "desc";
  emit("sort", "desc");
}

function withoutSort() {
  currentSort.value = "none";
  emit("sort", "none");
}
</script>

<style lang="scss" scoped>
.sort-panel {
  margin-bottom: 20px;
  border-radius: 10px;
}
.sort-title {
}
</style>
