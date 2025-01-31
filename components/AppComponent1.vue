<template>
  <div class="root-container">
    <!-- Nav Bar Div -->
    <div class="nav-bar-div">
      <UHorizontalNavigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />

      <nav class="nav-bar">
        <div class="nav-left">
          <UButton icon="i-heroicons-arrow-left" variant="ghost" @click="goBack" />
          <UButton icon="i-heroicons-arrow-path" variant="ghost" @click="refreshPage" />
          <UButton icon="i-heroicons-star" variant="ghost" />
          <span class="title">Browse Projects</span>
          <UInput
            loading
            icon="i-heroicons-magnifying-glass-20-solid"
            placeholder="Searching..."
          />
        </div>
      </nav>
    </div>

    <!-- Filter Bar Div -->
    <div class="filter-bar-div">
      <div class="filter-bar">
        <input type="text" placeholder="Keywords" class="filter-input" />
        
        <!-- Project Classification Dropdown using Set -->
        <USelect v-model="selectedClassification" :options="Array.from(classifications)" />

        <label class="favorite-label">
          <UCheckbox color="green" label="Favourite Category" :model-value="true" />
        </label>
        <UButton color="cyan" variant="soft">Search</UButton>
        <UButton color="cyan" variant="soft">Reset</UButton>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">


// Navigation links
const links = [
  { label: 'Category', icon: 'i-heroicons-home', to: '/getting-started/installation' },
  { label: 'Projects', icon: 'i-heroicons-chart-bar', to: '/components/horizontal-navigation' }
];

// Functions for navigation
const goBack = () => window.history.back();
const refreshPage = () => window.location.reload();

// Project Classification using Set
const classifications = new Set([
  'Construction1',
  'Construction2',
  'Infrastructure',
  'Technology',
  'Research',
  'Health'
]);

// Selected classification state
const selectedClassification = ref('Construction1');
</script>

<style scoped>
.filter-bar {
  display: flex;
  align-items: center;
  gap: 15px;
  flex-wrap: wrap;
}

.filter-input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 200px;
}

.favorite-label {
  display: flex;
  align-items: center;
  gap: 10px;
}

.nav-bar-div {
  padding: 15px;
}

.nav-left {
  display: flex;
  align-items: center;
  gap: 10px;
  width: 100%;
}
</style>
