<script setup lang="ts">
import type { Member } from "~/interfaces";

const route = useRoute();

const memberList = useState<Map<number, Member>>("memberList");
const member = computed((): Member => {
  const _id = Number(route.params.id);
  return memberList.value.get(_id) as Member;
});
</script>

<template>
  <section>
    <h3>会員詳細情報</h3>
    <dl>
      <dt>ID</dt>
      <dd>{{ member.id }}</dd>
      <dt>名前</dt>
      <dd>{{ member.name }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>ポイント</dt>
      <dd>{{ member.points }}</dd>
      <dt>備考</dt>
      <dd>{{ member.note ? member.note : "--" }}</dd>
    </dl>
  </section>
</template>
