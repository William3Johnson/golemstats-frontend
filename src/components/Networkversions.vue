<template>
  <div class="bg-white dark:bg-gray-800 pt-5 px-4 sm:px-6 shadow rounded-lg overflow-hidden">
    <div class="relative">
      <div class="absolute top-0 right-0 -mr-1 -mt-1 w-4 h-4 rounded-full bg-green-300 animate-ping"></div>
      <div class="absolute top-0 right-0 -mr-1 -mt-1 w-4 h-4 rounded-full bg-green-300"></div>
      <h1 class="text-2xl mb-2 font-medium dark:text-gray-300">Network Version Adoption</h1>

      <apexchart v-if="loaded" width="100%" height="350" type="bar" :options="chartOptions" :series="series"></apexchart>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loaded: false,
      series: [
        {
          data: [],
          name: "Providers",
        },
      ],
      chartOptions: {
        chart: {
          type: "bar",
          height: 350,
        },
        plotOptions: {
          bar: {
            borderRadius: 4,
            horizontal: false,
          },
        },
        yaxis: {
          title: {
            text: "Providers",
            rotate: -90,
            offsetX: 0,
            offsetY: 0,
            style: {
              color: undefined,
              fontSize: "12px",
              fontWeight: 600,
              cssClass: "apexcharts-yaxis-title",
            },
          },
        },
        xaxis: {
          title: {
            text: "Yagna Version",
            rotate: -90,
            offsetX: 0,
            offsetY: 0,
            style: {
              color: undefined,
              fontSize: "12px",
              fontWeight: 600,
              cssClass: "apexcharts-yaxis-title",
            },
          },
        },
        colors: ["#0000ff"],
        dataLabels: {
          enabled: false,
        },
      },
    }
  },
  created() {
    this.utilization()
  },
  mounted: function () {
    this.timer = setInterval(() => {
      if (document.visibilityState === "hidden") {
        return
      }
      this.utilization()
    }, 65000)
  },
  methods: {
    utilization() {
      this.series[0].data.length = 0
      this.axios.get("network/versions").then((response) => {
        let apiResponse = response.data

        apiResponse.forEach((obj, index) => {
          let versions = obj["version"]
          let count = obj["count"]

          this.series[0].data.push({
            x: versions,
            y: count,
          })
        })
      })

      this.loaded = true
    },
  },
}
</script>
