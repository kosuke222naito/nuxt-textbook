<script setup lang="ts">
import type { Member } from "~/interfaces";

definePageMeta({ layout: "member" });

const memberList = useState<Map<number, Member>>("memberList");
</script>

<template>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: 'index' }">TOP</NuxtLink></li>
      <li>会員リスト</li>
    </ul>
  </nav>
  <section>
    <h3>会員リスト</h3>
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
