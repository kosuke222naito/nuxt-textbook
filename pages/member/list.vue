<script setup lang="ts">
import type { Member } from "~/interfaces";

const PAGE_TITLE = "会員リスト";

definePageMeta({ layout: "member" });
useHead({ title: PAGE_TITLE });

const memberList = useState<Map<number, Member>>("memberList");
</script>

<template>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: 'index' }">TOP</NuxtLink></li>
      <li>{{ PAGE_TITLE }}</li>
    </ul>
  </nav>
  <section>
    <h3>{{ PAGE_TITLE }}</h3>
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
