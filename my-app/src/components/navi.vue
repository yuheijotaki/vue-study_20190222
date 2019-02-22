<template>
  <li><a href="javascript:void(0);" @click="emitEventOne">event01</a></li>
</template>

<script>
export default {
  name: 'navi',
  methods: {
    emitEventOne () {
      this.$emit('event-one')
    },
  }
}
</script>
