<template>
  <div class="container">
    <div class="wrapper">
      <div class="info">
        <h2 class="info__title">Messages</h2>
        <ul class="info__list">
          <li
            v-for="(message, index) in messages"
            :key="index"
            class="info__item"
          >
            <p class="info__description">
              {{ message }}
            </p>
          </li>
        </ul>
      </div>
    </div>
    <div class="poems">
      <Poems />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, nextTick } from "vue";
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

const jsonData = ref<string>("");
const messages = ref<string[]>([]);

onMounted(() => {
  Connect();
});
const Connect = async () => {
  try {
    const response = await axios.get<ResponseData>("http://127.0.0.1:5000");
    const data = response.data;
    await nextTick();

    jsonData.value = JSON.stringify(data, null, 2);

    messages.value = data.messages;

    await executeActionsWithDelay(data);
  } catch (error) {
    console.error(error);
  }
};

const executeActionsWithDelay = async (data: ResponseData) => {
  await replaceMessagesWithDelay(data.changes.replace.info);
  await deleteMessagesWithDelay(data.changes.delete);
};

const replaceMessagesWithDelay = async (replaceInfo: ReplaceInfo) => {
  for (const key in replaceInfo) {
    const changeInfo = replaceInfo[key];
    const indexToReplace = changeInfo.index;
    const newText = changeInfo.text;

    try {
      if (indexToReplace >= 0 && indexToReplace < messages.value.length) {
        await delay(1000);
        messages.value[indexToReplace] = newText;
      } else {
        console.error("Invalid indexToReplace:", indexToReplace);
      }
    } catch (error) {
      console.error("Error during replaceMessagesWithDelay:", error);
    }
  }
};

const deleteMessagesWithDelay = async (deleteIndices: DeleteInfo) => {
  try {
    for (const key in deleteIndices) {
      const indices = deleteIndices[key];

      if (Array.isArray(indices)) {
        indices.sort((a, b) => b - a);

        for (const deleteIndex of indices) {
          console.log("Deleting index:", deleteIndex);
          console.log("Current messages length:", messages.value.length);

          await delay(1000);

          if (deleteIndex >= 0 && deleteIndex < messages.value.length) {
            messages.value = messages.value.filter((_, index) => index !== deleteIndex);
          } else {
            console.error(`Invalid deleteIndex: ${deleteIndex}`);
          }
        }
      } else if (typeof indices === "number") {
        await delay(1000);

        if (indices >= 0 && indices < messages.value.length) {
          messages.value = messages.value.filter((_, index) => index !== indices);
        } else {
          console.error(`Invalid deleteIndex: ${indices}`);
        }
      } else {
        console.error(`Invalid indices for key ${key}:`, indices);
      }
    }
  } catch (error) {
    console.error("Error during deleteMessagesWithDelay:", error);
  }
};

const delay = (ms: number) => {
  return new Promise((resolve) => setTimeout(resolve, ms));
};
</script>

<style scoped lang="scss">
@use "@/assets/scss/fonts" as *;

.container {
  display: flex;
  font-family: Manrope, sans-serif;
  background-color: #f0f0f0;
  padding: 20px;
  justify-content: center;

  .wrapper {
    min-width: 900px;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    margin-right: 60px;
  }

  .info {
    margin-bottom: 20px;

    &__title {
      font-size: 18px;
      margin-bottom: 10px;
      color: #333;
    }

    &__description {
      @include manrope-font(1.5rem, normal);
    }

    &__list {
      list-style: none;
      padding: 0;

      &__item {
        border: 1px solid #ddd;
        margin-bottom: 10px;
        padding: 10px;
        border-radius: 4px;
      }
    }
  }

  .update-button {
    background-color: #4caf50;
    color: #fff;
    border: none;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    border-radius: 4px;

    &:hover {
      background-color: #45a049;
    }
  }
}
</style>