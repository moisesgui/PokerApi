<template>
  <div class="title">
    <h1 class="content">{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'TitleElement',
  props: {
    msg: String
  }
}
</script>

<style>
  .title {
    margin: 0 auto;
  }
  .content {
    padding: 16px 16px 0px;
  }
</style>