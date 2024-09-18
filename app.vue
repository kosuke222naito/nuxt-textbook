<script setup lang="ts">
import type { Member } from "~/interfaces";
import TheBaseSection from "./components/TheBaseSection.vue";

const memberListInit = new Map<number, Member>();

memberListInit.set(33456, {
  id: 33456,
  name: "田中太郎",
  email: "taro@example.com",
  points: 30,
});

memberListInit.set(47783, {
  id: 47783,
  name: "鈴木二郎",
  email: "jiro@example.com",
  points: 300,
  note: "ふがふが",
});

useState<Map<number, Member>>("memberList", () => memberListInit);
</script>

<template>
  <TheBaseSection />
</template>
