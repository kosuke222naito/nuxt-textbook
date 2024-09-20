<script setup lang="ts">
import type { Member } from "~/interfaces";

const SITE_TITLE = "ヘッダ変更サンプル";

useHead({ title: SITE_TITLE });

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

useState<Map<number, Member>>("memberList", () => memberListInit);
</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<style>
main {
  border: blue 1px solid;
  padding: 10px;
}

#breadcrumbs ul li {
  display: inline;
  list-style-type: none;
}

#breadcrumbs {
  margin-left: 0px;
}

#breadcrumbs ul {
  padding-left: 0px;
}

#breadcrumbs ul .current {
  color: red;
}

#breadcrumbs ul li:before {
  content: " > ";
}

#breadcrumbs ul li:first-child:before {
  content: none;
}
</style>
