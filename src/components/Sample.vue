<template>
  <div class="sample">
    <h1>{{ msg }}</h1>
    <p>this msg length is {{ msgLength }}</p>
    <input type="text" v-model="newMsg" />
    <button @click="update">更新</button>
    <button @click="repeat">繰り返す</button>
  </div>
</template>

<script>
import { mapState } from 'vuex';
import * as types from '@/store/mutation-types';
export default {
  name: 'Sample',
  data() {
    return {
    //   msg: 'Welcome to My Vuex Sample',
        newMsg: null
    };
  },
  computed: {
    // msg() {
    //   return this.$store.state.msg;
    // },
    msgLength() {
        return this.msg.length;
    },
    ...mapState({
        msg: state => state.msg,
    })
  },
  methods: {
    update() {
    //   this.$store.state.msg = this.newMsg;
        this.$store.commit(types.UPDATE_MESSAGE, this.newMsg);
    },
    repeat() {
        this.$store.dispatch('repeat');
    },
  }
};
</script>