<template>
  <div class="app">
    <main class="app__main main__wrapper">
      <div class="info">
        <ul class="main__list">
          <li v-for="(message, index) in messages" :key="index" class="main__item">
            <p class="item-list__description">
              {{ message }}
            </p>
          </li>
        </ul>
      </div>
      <div class="poems">
        <Poems />
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, defineProps } from "vue";
import axios from "axios";

interface ChangeInfo {
  index: number;
  text: string;
}

interface ReplaceInfo {
  [key: string]: ChangeInfo;
}

interface DeleteInfo {
  [key: string]: number[];
}

interface Changes {
  replace: { info: ReplaceInfo };
  delete: DeleteInfo;
}

interface ResponseData {
  changes: Changes;
  messages: string[];
}

const props = defineProps(["messages"]);
const messages = ref<string[]>(props.messages);

onMounted(async () => {
  try {
    const response = await axios.get<ResponseData>("http://localhost:8088");
    const data = response.data;

    await executeActionsWithDelay(data);
  } catch (error) {
    console.error(error);
  }
});

const executeActionsWithDelay = async (data: ResponseData) => {
  await replaceMessagesWithDelay(data.changes.replace.info);
  await deleteMessagesWithDelay(data.changes.delete);
};

const replaceMessagesWithDelay = async (replaceInfo: ReplaceInfo) => {
  for (const key in replaceInfo) {
    const changeInfo = replaceInfo[key];
    const indexToReplace = changeInfo.index;
    const newText = changeInfo.text;

    await delay(1000);
    messages.value[indexToReplace] = newText;
  }
};

const deleteMessagesWithDelay = async (deleteIndices: DeleteInfo) => {
  for (const key in deleteIndices) {
    const indices = deleteIndices[key];
    indices.sort((a, b) => b - a);

    for (const deleteIndex of indices) {
      await delay(1000);
      messages.value.splice(deleteIndex, 1);
    }
  }
};

const delay = (ms: number) => {
  return new Promise((resolve) => setTimeout(resolve, ms));
};
</script>

<style scoped lang="scss">
@use "@/assets/scss/fonts" as *;
</style>
