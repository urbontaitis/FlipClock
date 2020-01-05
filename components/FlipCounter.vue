<template>
  <div>
    <no-ssr>
      <flip-countdown :deadline="datetime" />
    </no-ssr>
  </div>
</template>

<script>
import FlipCountdown from 'vue2-flip-countdown'
import { format } from 'date-fns'

export default {
  components: { FlipCountdown },
  props: {
    minutes: { type: Number, required: true }
  },
  data() {
    return {
      date: new Date()
    }
  },
  computed: {
    datetime() {
      const minutes = this.minutes * 60 * 1000
      const minutesLater = this.date.getTime() + minutes
      return format(new Date(minutesLater), 'yyyy-MM-dd HH:mm:ss')
    }
  }
}
</script>
