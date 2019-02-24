<template>
  <li><a href="javascript:void(0);" @click="emitEventOne" class="naviLink">Front-end</a></li>
</template>

<script>
export default {
  name: 'navi',
  methods: {
    emitEventOne () {
      this.$emit('event-one',event)
    },
  }
}
</script>
