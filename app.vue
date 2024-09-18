<script setup lang="ts">
interface Member {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}

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

const memberList = ref(memberListInit);

const totalPoints = computed(() => {
  return [...memberList.value.values()].reduce((sum, member) => {
    return sum + member.points;
  }, 0);
});

const onIncrementPoints = (id: number): void => {
  const member = memberList.value.get(id);
  if (member != undefined) {
    member.points++;
  }
};
</script>

<template>
  <section>
    <h1>会員リスト</h1>
    <p>全会員の合計保有ポイント: {{ totalPoints }}</p>
    <OneMember
      v-for="[id, { name, email, points, note }] in memberList"
      :id
      :key="id"
      :name
      :email
      :points
      :note
      @incrementPoints="onIncrementPoints"
    />
  </section>
</template>
