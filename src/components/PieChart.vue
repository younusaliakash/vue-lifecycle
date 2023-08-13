<script setup>
import { onMounted, onBeforeUnmount } from "vue";
import Chart from "chart.js/auto";

let myPieChart;

onMounted(() => {
  const ctx = document.getElementById("my-pie-chart");

  myPieChart = new Chart(ctx, {
    type: "pie",
    data: {
      labels: ["Red", "Blue", "Yellow", "Green", "Navy"],
      datasets: [
        {
          label: "Pie Cart",
          data: [150, 50, 100, 75, 40],
          backgroundColor: [
            "rgb(255, 99, 132)",
            "rgb(54, 162, 235)",
            "rgb(255, 205, 86)",
            "rgb(0,128,0)",
            "#000080",
          ],
          hoverOffset: 4,
        },
      ],
    },
  });
});

onBeforeUnmount(() => {
  myPieChart.destroy();
});
</script>

<template>
  <div class="max-w-[720px] mx-auto py-8 px-4">
    <canvas id="my-pie-chart">
      <!-- ...  -->
    </canvas>
  </div>
</template>

<style scoped></style>
