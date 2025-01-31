<script setup lang="ts">

const columns = [
  { key: 'id', label: 'ID' },
  { key: 'url', label: 'URL' },
  { key: 'name', label: 'Project Name' },
  { key: 'status', label: 'Status' },
  { key: 'classification', label: 'Classification' },
  { key: 'column2', label: 'Phase' },
  { key: 'column3', label: 'Priority' }
];

const selectedColumns = ref([...columns]);


let people = ref([{
    "id": 101,
    "url": String,
    "name": String,
    "status": String,
    "classification": String,
    "column2": String,
    "column3": String
  }])


const q = ref('')

const filteredRows = computed(() => {
  if (!q.value) {
    return people.value; // Accessing the reactive array correctly
  }

  return people.value.filter((p) => {
    return Object.values(p).some((value) => {
      return String(value).toLowerCase().includes(q.value.toLowerCase());
    });
  });
});

const selected = ref([]);

onMounted(async () => {
  await getProjects();
});

async function getProjects() {
  const url = "http://localhost:3000/projects";
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    people.value = await response.json(); // Correctly updating the ref value
    console.log(people.value);
  } catch (error) {
    console.error(error.message);
  }
}

 
 
</script>

<template>
  <div>
    <div class="flex px-3 py-3.5 border-b border-gray-200 dark:border-gray-700">
      <UInput v-model="q" placeholder="Filter people..." />
    </div>

    <UTable v-model="selected" :rows="filteredRows" :columns="columns" />
  </div>
</template>

