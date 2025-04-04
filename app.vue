<script setup lang="ts">
import type { Member } from '@/interfaces';

useState<Map<number, Member>>(
  "memberList",
  (): Map<number, Member> => {
    const memberListInit = new Map<number, Member>();
    memberListInit.set(47783, {id: 47783, name: "鈴木次郎", email: "mue@example.com", points: 53});
    return memberListInit;
  }
)
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
#breadcrumbs ul {
  padding-left: 0;
}
#breadcrumbs ul .current {
  color: red;
}
#breadcrumbs ul li:before {
  content: ">";
}
#breadcrumbs ul li:first-child:before {
  content: none;
}
</style>
