<script setup lang="ts">
import type { Member } from "~/interfaces";

interface Props {
  id: number;
}

const { id } = defineProps<Props>();

const memberList = useState<Map<number, Member>>("memberList");
const member = memberList.value.get(id)!;

const pointsUp = (): void => {
  member.points++;
};
</script>

<template>
  <section class="box">
    <h4>{{ member.name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>名前</dt>
      <dd>{{ member.name }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ member.points }}</dd>
      <dt>備考</dt>
      <dd>{{ member.note ? member.note : "--" }}</dd>
    </dl>
    <button @click="pointsUp">ポイント加算</button>
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
