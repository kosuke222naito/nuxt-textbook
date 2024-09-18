<script setup lang="ts">
import type { Member } from "~/interfaces";

const memberList = useState<Map<number, Member>>("memberList");

const totalPoints = computed(() => {
  return [...memberList.value.values()].reduce((sum, member) => {
    return sum + member.points;
  }, 0);
});
</script>

<template>
  <section>
    <h1>会員リスト</h1>
    <p>全会員の合計保有ポイント: {{ totalPoints }}</p>
    <OneMember v-for="id in memberList.keys()" :key="id" :id />
  </section>
</template>

<style scoped>
section {
  border: orange 1px dashed;
  margin: 10px;
}
</style>
