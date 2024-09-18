<script setup lang="ts">
interface Props {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}

const { id, name, email, points, note = "--" } = defineProps<Props>();
const pointsDisplay = ref(points);

const pointUp = (): void => {
  pointsDisplay.value++;
};
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
      <dd>{{ pointsDisplay }}</dd>
      <dt>備考</dt>
      <dd>{{ note }}</dd>
    </dl>
    <button @click="pointUp">ポイント加算</button>
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
