<template>
  <div class="chart-container">
    <canvas id="lineChart"></canvas>
  </div>
</template>

<script setup>
import { Chart, registerables } from 'chart.js'
import ChartDataLabels from 'chartjs-plugin-datalabels'

Chart.register(...registerables, ChartDataLabels)

const chart = ref(null)
const allLabels = [
  'January', 'February', 'March', 'April', 'May', 'June', 
  'July', 'August', 'September', 'October', 'November', 'December'
];

onMounted(() => {
  const ctx = document.getElementById('lineChart').getContext('2d')
  chart.value = new Chart(ctx, {
    type: 'line',
    data: {
      labels: allLabels,
      datasets: [
        {
          label: 'Demo Line Dataset',
          data: [65, 59, 80, 81, 56, 55, 40, 66, 58, 90, 81, 76],
          fill: false,
          borderColor: 'rgb(75, 192, 192)',
          tension: 0.1,
          pointBackgroundColor: 'rgba(255, 99, 132, 0.5)',
          pointBorderColor: '#fff',
          pointBorderWidth: 2,
          pointRadius: 5,
          pointStyle: 'circle',
          borderWidth: 2,
        },
      ],
    },
    options: {
      scales: {
        y: {
          display: true, // Affiche l'axe Y
          grid: {
            drawBorder: false, // N'affiche pas la bordure de l'axe Y
            drawOnChartArea: false, // N'affiche pas les lignes de grille de l'axe Y
          },
          ticks: {
            display: true, // Affiche les labels de l'axe Y
            color: '#333', // Couleur des labels de l'axe Y
            font: {
              size: 14, // Taille de police des labels de l'axe Y
              family: 'Arial', // Police des labels de l'axe Y
            },
          },
        },
        x: {
          display: true, // Affiche l'axe X
          grid: {
            drawBorder: false, // N'affiche pas la bordure de l'axe X
            drawOnChartArea: false, // N'affiche pas les lignes de grille de l'axe X
          },
          ticks: {
            display: true, 
            color: '#333', 
            font: {
              size: 14, 
              family: 'Arial', 
            },
            callback: function (value, index, values) {
              return index % 3 === 0 ? value : ''; 
            },
          },
        },
      },
      plugins: {
        title: {
          display: true,
          text: 'Monthly Data',
          color: '#333',
          font: {
            size: 24,
            family: 'Arial',
          },
          padding: {
            top: 10,
            bottom: 30,
          },
          align: 'start',
        },
        legend: {
          display: true,
          position: 'right',
          align: 'end',
          labels: {
            usePointStyle: true,
            pointStyle: 'line',
            padding: 20,
            boxWidth: 20,
            textAlign: 'center',
            color: 'rgb(255, 99, 132)',
          },
        },
        datalabels: {
          align: 'end',
          anchor: 'end',
          backgroundColor: function (context) {
            return context.dataset.borderColor;
          },
          borderRadius: 4,
          color: 'white',
          formatter: Math.round,
          font: {
            family: 'Arial',
          },
        },
      },
    },
  })
})
</script>

<style scoped>
.chart-container {
  @apply flex justify-center items-center;
  position: relative;
  height: 40vh;
  width: 80vw;
  margin-left: 20px;
  margin-right: 20px;
}
</style>
