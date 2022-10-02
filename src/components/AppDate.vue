<template>
    <span :title="humanFriendlyDate(timestamp)">
        {{diffForHumans(timestamp)}}
    </span>
</template>

<script>
import dayjs from 'dayjs'
import relativeTime from 'dayjs/plugin/relativeTime'
import localizedDate from 'dayjs/plugin/localizedFormat'
dayjs.extend(relativeTime)
dayjs.extend(localizedDate)

export default {
  props: {
    timestamp: {
      required: true,
      type: Number
    }
  },
  methods: {
    diffForHumans (timestamp) {
      return dayjs.unix(timestamp).fromNow()
    },
    humanFriendlyDate (timestamp) {
      return dayjs.unix(timestamp).format('llll')
    }
  }
}
</script>

<style scoped>

</style>
