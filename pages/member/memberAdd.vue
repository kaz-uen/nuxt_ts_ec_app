<script setup lang="ts">
import type { Member } from '@/interfaces';

const router = useRouter();
const memberList = useState<Map<number, Member>>("memberList");
const member: Member = reactive(
  {
    id: 0,
    name: "",
    email: "",
    points: 0,
    note: ""
  }
)

const onAdd = (): void => {
  memberList.value.set(member.id, member);
  router.push({name: "member-memberList"});
}
</script>

<template>
  <h1>会員管理</h1>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{name: 'index'}">TOP</NuxtLink></li>
      <li><NuxtLink :to="{name: 'member-memberList'}">会員リスト</NuxtLink></li>
      <li>会員情報追加</li>
    </ul>
  </nav>
  <section>
    <h2>会員情報追加</h2>
    <p>情報を入力し、登録ボタンをクリックしてください。</p>
    <form v-on:submit.prevent="onAdd">
      <dl>
        <dt><label for="addId">ID</label></dt>
        <dd><input id="addId" type="number" v-model="member.id" required /></dd>
        <dt><label for="addName">名前</label></dt>
        <dd><input id="addName" type="text" v-model="member.name" required /></dd>
        <dt><label for="addEmail">メールアドレス</label></dt>
        <dd><input id="addEmail" type="email" v-model="member.email" required /></dd>
        <dt><label for="addPoints">保有ポイント</label></dt>
        <dd><input id="addPoints" type="number" v-model="member.points" required /></dd>
        <dt><label for="addNote">備考</label></dt>
        <dd><textarea id="addNote" v-model="member.note"></textarea></dd>
      </dl>
      <button type="submit">登録</button>
    </form>
  </section>
</template>
