<template>
  <div class="com-container">
    <div class="com-chart" ref="trend_ref"></div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      chartInstance: null
    }
  },
  mounted () {
    this.initChart()
    this.getData()
    window.addEventListener('resize', this.screenAdpter)
    this.screenAdpter()
  },
  destroyed () {
    window.removeEventListener('resize', this.screenAdpter)
  },
  methods: {
    initChart () {
      this.chartInstance = this.$echarts.init(this.$refs.trend_ref, 'chalk')
      const initOptions = {}
      this.chartInstance.setOption(initOptions)
    },
    async getData () {
      // const {data: ret} = await this.$http.get('trend')
      // console.log(ret)
      this.updateChart()
    },
    updateChart () {
      const dataOptions = {}
      this.chartInstance.setOption(dataOptions)
    },
    screenAdpter () {
      const adapterOption = {}
      this.chartInstance.setOption(adapterOption)
      this.chartInstance.resize()
    }
  }
}
</script>

<style>

</style>
