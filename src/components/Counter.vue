<template lang="pug">
.wrapper
  p.count
    | Count <output class="count-value">{{ count }}</output>
  .controls
    button.button.button-default(type="button" @click="increment()") Increment
    button.button.button-async(type="button" @click="incrementAsync()") Increment Async
</template>

<script>
import { mapGetters, mapActions, mapMutations } from 'vuex'
import {
  INCREMENT_COUNTER,
  INCREMENT_ASYNC_COUNTER
} from 'store/types'

export default {
  computed: mapGetters({
    count: 'count'
  }),

  methods: {
    ...mapActions({
      incrementAsync: INCREMENT_ASYNC_COUNTER
    }),
    ...mapMutations({
      increment: INCREMENT_COUNTER
    })
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  padding: 30px 0;
}

.count-value {
  font-size: 3.5rem;
}

.controls {
  margin-top: 15px;
}

.button {
  padding: 10px 30px;
  border: none;
  color: #fff;
  cursor: pointer;
  transition: background-color 200ms ease-out;
}

.button-default {
  background-color: #28c470;
}

.button-default:hover {
  background-color: #47d589;
}

.button-async {
  background-color: #ffa536;
}

.button-async:hover {
  background-color: #ffb55b;
}
</style>
