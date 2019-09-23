<template>

  <div class="box-main">
    <div class="content">
      <h1 class="title">¿Cuánto queda pa'l 18?</h1>
      <animated-number
      class="daysLeft"
      :value="daysLeft"
      :duration="1200"
      :round="1"
      />
      <div class="days">
        <span v-if="this.daysLeft === 0">días</span>
        <span v-else>días para el</span>
      </div>
      <div class="date">{{ date }}</div>
    </div>
  </div>

</template>

<script>

import * as moment from 'moment'
import AnimatedNumber from 'animated-number-vue'

export default {
  name: 'HelloWorld',
  data () {
    return {
      daysLeft: '0',
      date: '18 de Septiembre de 2020'
    }
  },
  components: {
    AnimatedNumber
  },
  methods: {
    getDaysLeft: function () {
      const year = new Date().getFullYear()
      const month = 8 // september
      const day = 18 // sum a day

      const months = [
        'Enero',
        'Febrero',
        'Marzo',
        'Abril',
        'Mayo',
        'Junio',
        'Julio',
        'Agosto',
        'Septiembre',
        'Octubre',
        'Noviembre',
        'Diciembre'
      ]

      let eventDate = moment([year, month, day])
      const todaysDate = moment()

      if (todaysDate.isAfter(eventDate)) {
        eventDate = eventDate.add(1, 'Y')
      }

      const daysleft = eventDate.diff(todaysDate, 'days')

      if (daysleft === 0) {
        this.daysLeft = 0
        this.date = '¡Hoy es 18! ¡Tiki-tiki-tiiii!'
      } else {
        this.daysLeft = daysleft
      }
    }
  },
  created: function () {
    this.getDaysLeft()
  }
}

</script>

<style lang="scss" scoped>

.box-main {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 85%;
  height: 70%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  background-color: rgba(0, 0, 0, .7);
  color: #fff;
  text-align: center;
  border-radius: 6px;

  .title {}

  .daysLeft {
    font-size: 10rem;
    line-height: .6;
    font-weight: bold;
    letter-spacing: -.05em;
  }

  .days {
    font-size: 2em;
  }

  .date {
    margin-top: 2rem;
    font-size: 2.5em;
  }
}

</style>
