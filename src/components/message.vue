<script>
export default {
  props: {
    message: Object,
    lastUser: String,
  },
};
</script>

<template>
  <div class="layout">
    <div class="pp"></div>
    <div class="message">
      <div class="nick-time">
        <div class="nick">{{ message.username }}</div>
        <span class="date">{{ ("" + new Date()).substring(4, 25) }}</span>
      </div>
      <div class="text">{{ message.text }}</div>
    </div>
  </div>
</template>

<style>
.layout {
  height: auto;
  width: 96%;
  margin: 2%;
  display: flex;
  justify-content: start;
  color: black;
  font-size: 18px;
  text-align: start;
}
.pp {
  height: 40px;
  width: 40px;
  border-radius: 100%;
  background-color: purple;
}
.layout > .message {
  max-width: 100%;
  height: auto;
  width: 90%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: 3%;
  padding: 0%;
  text-align: start;
}
.nick-time {
  width: auto;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
}
.nick-time > .nick {
  width: auto;
  display: flex;
  margin: 0% 12px 0% 0%;
  font-size: 1em;
  color: deeppink;
  font-weight: bold;
}
.nick-time > .date {
  font-size: 14px;
}
.message > .text {
  word-break: break-all;
}
</style>