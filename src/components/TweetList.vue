<script setup lang="ts">
import { ref } from "vue";

type Tweet = {
  id: number;
  description: string;
};
type Props = {
  tweets: Tweet[];
};

const inputtingDesc = ref<string>("");

defineProps<Props>();

const emit = defineEmits(["delete-tweet"]);
const deleteTweet = (id: number) => {
  emit("delete-tweet", id);
  //   tweets.value = tweets.value.filter((t) => t.id !== id);
};
</script>

<template>
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">DELETE</button>
  </li>
</template>

<style scoped>
.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: ghostwhite;
  padding: 8px 20px;
  width: 300px;
}

.delete-button {
  color: white;
  font-weight: bold;
  background-color: rgb(186, 171, 55);
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.delete-button:hover {
  background-color: rgb(120, 110, 36);
}
</style>
