<script setup lang="ts">
import { ref } from "vue";

const inputtingDesc = ref<string>("");

const emit = defineEmits(["post-tweet"]);

// 子コンポーネントから親コンポーネントへ伝搬
// post-tweetというメソッドでinputtingDesc.valueを引数に持つ
// 親で受け取る　@post-tweet
const postTweet = () => {
  emit("post-tweet", inputtingDesc.value);
};
</script>

<template>
  <div class="form-container">
    <input v-model="inputtingDesc" />
    <button class="save-button" @click="postTweet">Post</button>
  </div>
</template>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

.save-button {
  color: white;
  font-weight: bold;
  background-color: aquamarine;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
  margin-top: 12px;
}
.save-button:hover {
  background-color: aqua;
}
</style>
