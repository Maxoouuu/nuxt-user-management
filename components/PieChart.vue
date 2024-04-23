<template>
  <div class="chart-container p-8 max-w-xs max-h-xs mx-auto">
    <canvas id="pieChart"></canvas>
  </div>
</template>

<script setup>
import { Chart, registerables } from 'chart.js'

Chart.register(...registerables)

onMounted(() => {
  const ctx = document.getElementById('pieChart').getContext('2d')
  const pieChart = new Chart(ctx, {
    type: 'pie',
    data: {
      labels: ['Red', 'Blue', 'Yellow'],
      datasets: [
        {
          label: 'My First Dataset',
          data: [300, 50, 100],
          backgroundColor: [
            'rgb(255, 99, 132)',
            'rgb(54, 162, 235)',
            'rgb(255, 205, 86)',
          ],
          hoverOffset: 4,
        },
      ],
    },
  })
})
</script>

<style scoped>
.chart-container {
  @apply flex justify-center items-center;
}
</style>
