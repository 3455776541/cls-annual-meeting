<template>
  <div class="foot-wrapper">
    <input class="chat-input" type="text" name="" v-model="msg" @keyup.enter="send(msg);">
    <span class="chat-sub" :class="{'primary':!!msg}" @click="send(msg)">发送</span>
  </div>
</template>

<script>
import CHAT from '../../api/chat'
export default {
  name: 'ChatFoot',
  data () {
    return {
      msg: ''
    }
  },
  ready () {
    CHAT.init()
    console.log(CHAT, 'ww')
  },
  methods: {
    send (msg) {
      CHAT.submit(msg)
      this.msg = ''
      console.log(CHAT)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .foot-wrapper{
    background-color: #f1f1f1;
    height: 80px;
    flex-shrink: 0;
    display: flex;
    padding: 10px 20px;
    justify-content: space-between;
    border-top: solid 1px rgba(0,0,0,0.1);
    font-size: 32px;
  }
  .foot-wrapper .chat-input{
    height: 100%;
    width: 80%;
    border-radius: 20px;
    outline: none;
    border:none;
    box-sizing: border-box;
    padding: 10px;
    font-size: 44px;
    color: #333;
  }
  .foot-wrapper .chat-sub{
    display: flex;
    background-color: rgba(0,0,0,0.1);
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 18%;
    border-radius: 20px;
    outline: none;
  }
  /*.primary{*/
  /*background-color: #3CAF36;*/
  /*}*/
</style>
