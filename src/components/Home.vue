<template>

  <div class="box-main">
    <h1 class="title">¿Cuánto queda pa'l 18?</h1>
    <animated-number
    class="daysLeft"
    :value="daysLeft"
    :duration="2000"
    :round="1"
    />
    <!-- <div class="daysLeft">{{ daysLeft }}</div> -->
    <div class="days">días para el</div>
    <div class="date">{{ date }}</div>
  </div>

</template>

<script>

import * as moment from 'moment'
import AnimatedNumber from 'animated-number-vue'

export default {
  name: 'HelloWorld',
  data () {
    return {
      daysLeft: '290',
      date: '18 de Septiembre de 2019'
    }
  },
  components: {
    AnimatedNumber
  },
  methods: {
    getDaysLeft: function () {
      const year = new Date().getFullYear()
      const month = 8 // Septiembre
      const day = 18

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

      this.date = `${day} de ${months[month]} de ${year}`

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
  padding: 1rem;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 85%;
  height: 85%;
  background-color: rgba(0, 0, 0, .8);
  color: #fff;
  text-align: center;
  border-radius: 6px;

  .title {}

  .daysLeft {
    font-size: 10rem;
    line-height: 1;
  }

  .days {
    font-size: 2em;
  }

  .date {
    margin-top: 2rem;
    font-size: 3em;
  }
}

</style>
