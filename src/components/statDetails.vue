<template>
    
</template>

<script>
    export default {
        name: "statDetails",
      props: {
        hp: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        stamina: {
          type: Object,
          required: true,
          validator(value) {
            return (typeof value.current === 'number') && (typeof value.max === 'function')
              && value.current <= 15 && value.max() === 15 && Number.isInteger(value.current)
          }
        },
        atk: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        def: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        crit: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        critDmg: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        acc: {
          type: Number,
          required: true,
          validator(value) {
            return Number.isInteger(value)
          }
        },
        dodge: {
          type: Number,
          validator(value) {
            return Number.isInteger(value)
          }
        }
      }
    }
</script>

<style scoped>

</style>
