<script setup lang="ts">
// import type { Member } from '@/interfaces';

const PAGE_TITLE = "会員リスト";

useHead({
  title: PAGE_TITLE,
})

definePageMeta({
  layout: "member"
})

const asyncData = useLazyFetch("/api/getMemberList");
const memberList = asyncData.data;
const pending = asyncData.pending;

// const memberList = useState<Map<number, Member>>("memberList");
</script>

<template>
  <nav id="breadcrumbs">
    <ul>
      <li><NuxtLink :to="{name: 'index'}">TOP</NuxtLink></li>
      <li>{{ PAGE_TITLE }}</li>
    </ul>
  </nav>
  <section>
    <h2>{{ PAGE_TITLE }}</h2>
    <p>新規登録は<NuxtLink :to="{name: 'member-memberAdd'}">こちら</NuxtLink>から</p>
    <p v-if="pending">データ取得中...</p>
    <section v-else>
      <ul>
        <li
          v-for="member in memberList"
          v-bind:key="member.id"
        >
          <NuxtLink :to="{name: 'member-memberDetail-id', params: {id: member.id}}">
            IDが{{ member.id }}の{{ member.name }}さん
          </NuxtLink>
        </li>
      </ul>
    </section>
  </section>
</template>
