<template>
  <div style="display: flex; gap: 4em; font-family: sans-serif">
    <div style="display: inline-block">
      <h1>publish value as boolean</h1>
      <h2>❎ published only</h2>
      <div v-for="article of queryResult1" :key="`${article.path}-1`">
        <ContentRenderer :value="article" />
      </div>

      <h2>❎ unpublished only</h2>
      <div v-for="article of queryResult2" :key="`${article.path}-2`">
        <ContentRenderer :value="article" />
      </div>

      <h2>✅ all</h2>
      <div v-for="article of queryResult3" :key="`${article.path}-3`">
        <ContentRenderer :value="article" />
      </div>
    </div>
    <div style="background-color: #ccc; width: 0.2em"></div>

    <div style="display: inline-block">
      <h1>publish value as string</h1>
      <h2>✅published only</h2>
      <div v-for="article of queryResult4" :key="`${article.path}-1`">
        <ContentRenderer :value="article" />
      </div>

      <h2>✅ unpublished only</h2>
      <div v-for="article of queryResult5" :key="`${article.path}-2`">
        <ContentRenderer :value="article" />
      </div>

      <h2>✅ all</h2>
      <div v-for="article of queryResult6" :key="`${article.path}-3`">
        <ContentRenderer :value="article" />
      </div>
    </div>
    <div style="background-color: #ccc; width: 0.2em"></div>

    <div style="display: inline-block">
      <h1>publish value as boolean with int workaround</h1>
      <h2>✅ published only</h2>
      <div v-for="article of queryResult7" :key="`${article.path}-1`">
        <ContentRenderer :value="article" />
      </div>

      <h2>✅ unpublished only</h2>
      <div v-for="article of queryResult8" :key="`${article.path}-2`">
        <ContentRenderer :value="article" />
      </div>

      <h2>✅ all</h2>
      <div v-for="article of queryResult9" :key="`${article.path}-3`">
        <ContentRenderer :value="article" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { data: queryResult1 } = await useAsyncData(
  () => queryCollection("articlesBoolean").where("published", "=", true).all(),
  { server: false },
);

const { data: queryResult2 } = await useAsyncData(() =>
  queryCollection("articlesBoolean").where("published", "=", false).all(),
);

const { data: queryResult3 } = await useAsyncData(() =>
  queryCollection("articlesBoolean").all(),
);

const { data: queryResult4 } = await useAsyncData(() =>
  queryCollection("articlesString").where("published", "=", "true").all(),
);

const { data: queryResult5 } = await useAsyncData(() =>
  queryCollection("articlesString").where("published", "=", "false").all(),
);

const { data: queryResult6 } = await useAsyncData(() =>
  queryCollection("articlesString").all(),
);

const { data: queryResult7 } = await useAsyncData(() =>
  queryCollection("articlesBoolean").where("published", "=", 1).all(),
);

const { data: queryResult8 } = await useAsyncData(() =>
  queryCollection("articlesBoolean").where("published", "=", 0).all(),
);

const { data: queryResult9 } = await useAsyncData(() =>
  queryCollection("articlesBoolean").all(),
);
</script>
