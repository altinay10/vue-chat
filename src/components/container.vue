<script>
import messageComponent from "./message.vue";

export default {
  data() {
    return {
      messages: [],
      message: { username: "", text: "" },
      username: "",
      text: "",
      conn: "",
    };
  },
  components: {
    messageComponent,
  },
  methods: {
    sendMsg() {
      if (this.text.split("").some((x) => x != " ")) {
        this.conn.send(
          JSON.stringify({ username: this.username, text: this.text })
        );
      }
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
  created() {
    this.username = window.prompt("Enter Username");
  },
  mounted() {
    this.conn = new WebSocket("ws://192.168.1.34:8000/ws/" + this.makeid(20));
    this.conn.onmessage = (event) => {
      this.message = JSON.parse(event.data);
      this.messages.push(this.message);
      this.text = "";
    };
  },
};
</script>

<template>
  <div class="root">
    <div class="container">
      <messageComponent
        v-for="(message, i) in messages"
        :key="i"
        :message="message"
        :lastUser="
          messages.length >= 2 ? messages[messages.length - 2].username : null
        "
      />
    </div>
    <input
      @keypress.enter="sendMsg()"
      v-model="text"
      type="text"
      id="text-input"
      placeholder="Enter your message"
    />
  </div>
</template>

<style>
.root {
  height: 100%;
  width: 50%;
  margin: 0%;
  background: linear-gradient(135deg, #7886ff, #8ddbf3);
  box-shadow: -1px -20px 20px 10px #3d6dff6e;
}
.root input {
  height: 6%;
  width: 100%;
  margin: 0px;
  padding-left: 2%;
  background-color: rgba(18, 179, 104, 0.911);
  box-sizing: border-box;
  border-width: 0px;
  outline: none;
  font-size: 18px;
}
.container {
  height: 94%;
  width: 100%;
  padding: 0px;
  overflow: auto;
  scroll-behavior: smooth;
  text-align: start;
}
.container p {
  max-width: 90%;
  color: black;
  margin: 15px;
  font-size: 20px;
  text-align: start;
  margin-right: 40px;
}
</style>