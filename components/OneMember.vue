<script setup lang="ts">
import type { Member } from "~/interfaces";

interface Props {
  id: number;
}

const { id } = defineProps<Props>();

const memberList = useState<Map<number, Member>>("memberList");
const { name, email, points, note = "" } = memberList.value.get(id)!;

const pointsRef = ref(points);
</script>

<template>
  <section class="box">
    <h4>{{ name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>名前</dt>
      <dd>{{ name }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ pointsRef }}</dd>
      <dt>備考</dt>
      <dd>{{ note }}</dd>
    </dl>
    <button @click="pointsRef++">ポイント加算</button>
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
