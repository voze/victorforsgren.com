<template>
  <section class="container">
    <post-view v-bind:post="post"></post-view>
    <adsbygoogle/>
  </section>
</template>

<script>
import PostView from '~/components/PostView.vue'
import { getPost } from '../../assets/post.js'

export default {
  components: {
    PostView
  },
  data() {
    return {
      post: null
    }
  },
  async asyncData({params, error}) {
    let post = await getPost(params.id)
    if (!post) return error({statusCode: 404, message: "Post not found"});
    return {post}
  }
}
</script>