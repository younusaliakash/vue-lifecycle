<script>
import { ref, onMounted } from "vue";

export default {
  name: "DataFetchingComponent",
  setup() {
    const loading = ref(true);
    const data = ref([]);

    // Function to make the API call
    const fetchData = async () => {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        const result = await response.json();
        data.value = result;
        loading.value = false;
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    };

    // Call fetchData when the component is mounted
    onMounted(() => {
      fetchData();
    });

    return {
      loading,
      data,
    };
  },
};
</script>

<template>
  <div v-for="(item, idx) in data" :key="idx">
    <h2>Title : {{ item.name }}</h2>
    <br />
  </div>
</template>

<style scoped></style>
