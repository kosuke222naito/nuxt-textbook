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
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: 'member-list' }">会員リスト</NuxtLink></li>
      <li>会員詳細情報</li>
    </ul>
  </nav>
  <section>
    <h2>会員詳細情報</h2>
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
