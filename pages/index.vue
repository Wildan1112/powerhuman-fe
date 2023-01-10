<template>
  <Tutorial />
</template>

<script>

export default {
  name: 'IndexPage',
  async asnyData({ params }) {
    const post = await axios.get('https://api.nuxtjs.dev/posts/1')
    return { post }
  }
}
</script>
