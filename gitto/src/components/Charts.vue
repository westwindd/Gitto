<!-- src/components/Charts.vue -->
<template>
    <section class="charts mt-4">
      <div class="row">
        <div class="col-lg-6 mb-4" v-for="chart in chartDataSets" :key="chart.id">
          <div class="chart-container rounded-2 p-3">
            <h3 class="fs-6 mb-3">{{ chart.title }}</h3>
            <canvas :id="chart.id"></canvas>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { Chart, registerables } from 'chart.js';
  Chart.register(...registerables);
  
  export default {
    name: "Charts-home",
    data() {
      return {
        chartDataSets: [
          {
            id: "myChart",
            title: "Chart title number one",
          },
          {
            id: "myChart2",
            title: "Chart title number two",
          },
          {
            id: "chart3",
            title: "Chart title number three",
          },
        ],
      };
    },
    mounted() {
      this.initCharts();
    },
    methods: {
      initCharts() {
        // Chart 1: Bar Chart
        new Chart(document.getElementById('myChart'), {
          type: 'bar',
          data: {
            labels: ["January", "February", "March", "April", 'May', 'June', 'August', 'September'],
            datasets: [
              {
                label: "Lost",
                data: [45, 25, 40, 20, 60, 20, 35, 25],
                backgroundColor: "#0d6efd",
                borderColor: 'transparent',
                borderWidth: 2.5,
                barPercentage: 0.4,
              },
              {
                label: "Success",
                data: [20, 40, 20, 50, 25, 40, 25, 10],
                backgroundColor: "#dc3545",
                borderColor: 'transparent',
                borderWidth: 2.5,
                barPercentage: 0.4,
              },
            ],
          },
          options: {
            scales: {
              y: {
                grid: {
                  color: '#3b3d56',
                  zeroLineColor: '#3b3d56',
                },
                ticks: {
                  stepSize: 15,
                },
              },
              x: {
                grid: {
                  display: false,
                },
              },
            },
            responsive: true,
            maintainAspectRatio: false,
          },
        });
  
        // Chart 2: Line Chart
        new Chart(document.getElementById('myChart2'), {
          type: 'line',
          data: {
            labels: ["January", "February", "March", "April", 'May', 'June', 'August', 'September'],
            datasets: [
              {
                label: "Dataset 1",
                data: [4, 20, 5, 20, 5, 25, 9, 18],
                backgroundColor: 'transparent',
                borderColor: '#0d6efd',
                tension: 0.4,
                borderWidth: 1.5,
              },
              {
                label: "Dataset 2",
                data: [11, 25, 10, 25, 10, 30, 14, 23],
                backgroundColor: 'transparent',
                borderColor: '#dc3545',
                tension: 0.4,
                borderWidth: 1.5,
              },
              {
                label: "Dataset 3",
                data: [16, 30, 16, 30, 16, 36, 21, 35],
                backgroundColor: 'transparent',
                borderColor: '#f0ad4e',
                tension: 0.4,
                borderWidth: 1.5,
              },
            ],
          },
          options: {
            scales: {
              y: {
                grid: {
                  drawBorder: false,
                  color: '#3b3d56',
                },
                ticks: {
                  stepSize: 12,
                },
              },
              x: {
                grid: {
                  display: false,
                },
              },
            },
            responsive: true,
            maintainAspectRatio: false,
          },
        });
  
        // Chart 3: Multiple Line Chart
        new Chart(document.getElementById('chart3'), {
          type: 'line',
          data: {
            labels: ["One", "Two", "Three", "Four", "Five", 'Six', "Seven", "Eight"],
            datasets: [
              {
                label: "Lost",
                tension: 0.2,
                borderColor: '#d9534f',
                borderWidth: 1.5,
                data: [3, 30, 16, 30, 16, 36, 21, 40],
                backgroundColor: 'transparent',
              },
              {
                label: "Success",
                tension: 0.2,
                borderColor: '#5cb85c',
                borderWidth: 1.5,
                data: [6, 20, 5, 20, 5, 25, 9, 18],
                backgroundColor: 'transparent',
              },
              {
                label: "Pending",
                tension: 0.2,
                borderColor: '#f0ad4e',
                borderWidth: 1.5,
                data: [12, 20, 15, 20, 5, 35, 10, 15],
                backgroundColor: 'transparent',
              },
              {
                label: "Completed",
                tension: 0.2,
                borderColor: '#337ab7',
                borderWidth: 1.5,
                data: [16, 25, 10, 25, 10, 30, 14, 23],
                backgroundColor: 'transparent',
              },
            ],
          },
          options: {
            scales: {
              y: {
                grid: {
                  drawBorder: false,
                  color: '#3b3d56',
                },
                ticks: {
                  stepSize: 12,
                },
              },
              x: {
                grid: {
                  display: false,
                },
              },
            },
            responsive: true,
            maintainAspectRatio: false,
          },
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .chart-container {
    background-color: var(--dk-dark-bg);
    height: 300px;
  }
  
  .chart-container h3 {
    color: var(--dk-gray-400);
  }
  </style>
  