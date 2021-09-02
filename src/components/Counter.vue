<template>
  <div class="flex flex-col justify-center items-center py-40">
    <section class="text-3xl flex justify-center content-center flex-col mx-auto my-4 text-center mb-16">
      <h4 v-if="!done">BUY NOW</h4>
      <h4 v-else>TIME OVER</h4>
    </section>

    <section class="flex text-6xl justify-center content-center" v-if="loaded">
      <div class="days mr-2 relative ">
        <div class="bg-indigo-900 px-4 py-4 mb-4 rounded">{{ display.days }}</div>
        <div class="label text-sm bottom-0  px-4">{{ displayText.days }}</div>
      </div>
      <span>:</span>
      <div class="hours mx-2 relative ">
        <div class="bg-indigo-900 px-4 py-4 mb-4  rounded">{{ display.hours }}</div>
        <div class="label text-sm absolute bottom-0  px-4">{{ displayText.hours }}</div>
      </div>
      <span>:</span>
      <div class="minutes mx-2 relative">
        <div class="bg-indigo-900 px-4 py-4 mb-4  rounded">{{ display.minutes }}</div>
        <div class="label text-sm absolute bottom-0  px-4">{{ displayText.minutes }}</div>
      </div>
      <span>:</span>
      <div class="seconds ml-2 relative">
        <div class="bg-indigo-900 px-4 py-4 mb-4  rounded">{{ display.seconds }}</div>
        <div class="label text-sm absolute bottom-0 px-4">{{ displayText.seconds }}</div>
      </div>
    </section>

  </div>
</template>

<script>
export default {
    data() {
      return {
        display: {
          days: 0,
          hours: 0,
          minutes: 0,
          seconds: 0,
        },
        displayText: {
          days: 'DAYS',
          hours: 'HOURS',
          minutes: 'MINUTES',
          seconds: 'SECONDS',
        },
        loaded: false,
        done: false,
      }
    },
    computed: {
      seconds() {
        return 1000
      },
      minutes() {
        return this.seconds * 60
      },
      hours() {
        return this.minutes * 60
      },
      days() {
        return this.hours * 24
      },
      end() {
        return new Date(
          this.year,
          this.month,
          this.day,
          this.hour,
          this.minute,
          this.second,
          this.millisecond,
        )
      },
    },
    mounted() {
      this.showRemaining()
    },
    methods: {
      formatNumber(number) {
        return number < 10 ? '0' + number : number
      },
      showRemaining() {
        const timer = setInterval (() => {
          const now = new Date()
          //const end = new Date(2021, 8, 14, 18, 10, 10, 10)
          const distance = this.end.getTime() - now.getTime()

          if(distance < 0) {
            clearInterval(timer)
            this.done = true
            return
          }

          const timerDays = Math.floor(distance / this.days)
          const timerHours = Math.floor((distance % this.days) / this.hours)
          const timerMinutes = Math.floor((distance % this.hours) / this.minutes)
          const timerSeconds = Math.floor((distance % this.minutes) / this.seconds)

          this.display.minutes = this.formatNumber(timerMinutes)
          this.display.seconds = this.formatNumber(timerSeconds)
          this.display.hours = this.formatNumber(timerHours)
          this.display.days = timerDays

          this.loaded = true
      }, 1000)
    }
  },
  props: ['year', 'month', 'day', 'hour', 'minute', 'second', 'millisecond'],
}
</script>

<style>

</style>