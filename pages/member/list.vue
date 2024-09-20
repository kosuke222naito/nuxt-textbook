<script setup lang="ts">
import type { Member } from "~/interfaces";

const memberList = useState<Map<number, Member>>("memberList");
</script>

<template>
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: 'index' }">TOP</NuxtLink></li>
      <li>会員リスト</li>
    </ul>
  </nav>
  <section>
    <h2>会員リスト</h2>
    <p><NuxtLink :to="{ name: 'member-list-add' }">新規登録</NuxtLink></p>
    <ul>
      <li v-for="[id, { name }] in memberList" :key="id">
        <NuxtLink :to="{ name: 'member-list-id', params: { id } }">
          {{ id }}: {{ name }}
        </NuxtLink>
      </li>
    </ul>
  </section>
  <NuxtPage />
</template>
