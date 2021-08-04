<script>
import messageComponent from "./message.vue";

export default {
  data() {
    return {
      messages: [],
      message: "",
      conn: "",
    };
  },
  components: {
    messageComponent,
  },
  methods: {
    sendMsg() {
      this.conn.send(this.message);
      console.log("bura çalıştı");
    },
    makeid(length) {
      var result = "";
      var characters =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      var charactersLength = characters.length;
      for (var i = 0; i < length; i++) {
        result += characters.charAt(
          Math.floor(Math.random() * charactersLength)
        );
      }
      return result;
    },
  },
  mounted() {
    this.conn = new WebSocket("ws://192.168.1.34:8000/ws/" + this.makeid(20));
    this.conn.onmessage = (event) => {
      console.log(event.data);
      this.message = event.data;
      this.messages.push(this.message);
      this.message = "";
    };
  },
};
</script>

<template>
  <div class="root">
    <div class="container">
      <p>Welcome to Chat</p>
      <messageComponent
        v-for="message in messages"
        :key="message"
        v-text="message"
      />
    </div>
    <input
      @keypress.enter="sendMsg()"
      v-model="message"
      type="text"
      id="text-input"
      placeholder="Enter your message"
    />
  </div>
</template>

<style>
body {
  height: 100%;
  width: 100%;
  margin: 0px;
  padding: 0px;
  scroll-behavior: none;
  display: flex;
  justify-content: center;
}
.root {
  margin: 0px;
  width: 500px;
  height: 100%;
  background-color: rgba(15, 146, 197, 0.911);
}
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-thumb {
  background: crimson;
  border-radius: 10px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 15px gold;
  border-radius: 10px;
}
.container {
  width: 500px;
  height: 94%;
  padding: 0px;
  overflow: auto;
  scroll-behavior: smooth;
  text-align: start;
}
.container p {
  color: black;
  margin: 15px;
  font-size: 18px;
  text-align: center;
}
.root input {
  margin: 0px;
  padding-left: 10px;
  width: 100%;
  box-sizing: border-box;
  height: 6%;
  border-width: 0px;
  background-color: rgba(18, 179, 104, 0.911);
  outline: none;
  font-size: 18px;
}
</style>