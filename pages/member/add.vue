<script setup lang="ts">
import type { Member } from "~/interfaces";

const router = useRouter();

const memberList = useState<Map<number, Member>>("memberList");
const member: Ref<Member> = ref({
  id: 0,
  name: "",
  email: "",
  points: 0,
  note: "",
});

const onAdd = (): void => {
  memberList.value.set(member.value.id, member.value);
  router.push({ name: "member-list" });
};
</script>

<template>
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{ name: 'index' }">TOP</NuxtLink></li>
      <li><NuxtLink :to="{ name: 'member-list' }">会員リスト</NuxtLink></li>
      <li>会員情報追加</li>
    </ul>
  </nav>
  <section>
    <h2>会員情報追加</h2>
    <p>情報を入力し、登録ボタンをクリックしてください</p>
    <form @submit.prevent="onAdd">
      <dl>
        <dt><label for="addId">ID&nbsp;</label></dt>
        <dd>
          <input type="number" id="addId" v-model.number="member.id" required />
        </dd>
        <dt><label for="addName">名前&nbsp;</label></dt>
        <dd>
          <input type="text" id="addName" v-model.trim="member.name" required />
        </dd>
        <dt><label for="addEmail">メールアドレス&nbsp;</label></dt>
        <dd>
          <input type="email" id="addEmail" v-model="member.email" required />
        </dd>
        <dt><label for="addPoints">ポイント&nbsp;</label></dt>
        <dd>
          <input
            type="number"
            id="addPoints"
            v-model="member.points"
            required
          />
        </dd>
        <dt><label for="addNote">備考&nbsp;</label></dt>
        <dd>
          <textarea id="addNote" v-model="member.note"></textarea>
        </dd>
      </dl>
      <button type="submit">登録</button>
    </form>
  </section>
</template>
