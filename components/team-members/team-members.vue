<template>
  <ul v-if="posts.length > 0" class="cards">
    <li
      v-for="(post, index) in posts"
      :key="index"
    >
    <template v-if="postType === 'team'">
      <div class="column">
          <img
           v-if="post.avatar"
           style="width: 500px; height: 300px"
           :src="post.avatar"
          >
         <div class="container">
          <h2>{{ post.name }}</h2>
          <p class="description">{{ post.title }}</p>
         </div>
        </div>
    </template>
    </li>
  </ul>
  <div v-else-if="loading" class="cards">
    <div v-for="placeholder in placeholderClasses" :key="placeholder.id" class="card">
      <content-placeholders :rounded="true" :class="placeholder">
        <content-placeholders-heading />
      </content-placeholders>
    </div>
  </div>
  <p v-else class="max-w-5xl mx-auto">
    {{ amount > 1 ? 'Posts not found' : 'Post not found' }}
  </p>
</template>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<script>
  export default {
    name: 'Posts',
    props: {
      postType: {
        type: String,
        default: 'project',
        validator: (val) => ['team' ].includes(val),
      },
      amount: { // ? https://content.nuxtjs.org/fetching#limitn
        type: Number,
        default: 10,
        validator: (val) => val >= 0 && val < 100,
      },
      sortBy: { // ? https://content.nuxtjs.org/fetching#sortbykey-direction
        type: Object,
        default: () => ({
          key: 'slug',
          direction: 'desc' // you probably want 'asc' here
        }),
        validator: (obj) => typeof obj.key === 'string' && typeof obj.direction === 'string',
      }
    },
    data() {
      return {
        posts: [],
        loading: true,
      }
    },
    computed: {
      placeholderClasses() {
        const classes = ['w-full','w-2/3','w-5/6'];
        return [...Array.from({ length: this.amount }, (v, i) => classes[i % classes.length])]; // repeats classes after one another
      }
    },
    async mounted() {
      this.loading = true;
      this.posts = await this.fetchPosts();
      this.loading = false;
    },
    methods: {
      formatDate(dateString) {
        const date = new Date(dateString)
        return date.toLocaleDateString(process.env.lang) || ''
      },
      async fetchPosts(
          postType = this.postType,
          amount = this.amount,
          sortBy = this.sortBy,
        ) {
        return this.$content(postType)
          .sortBy(sortBy.key, sortBy.direction)
          .limit(amount)
          .fetch()
          .catch((err) => {
            error({ statusCode: 404, message: amount > 1 ? 'Posts not found' : 'Post not found' })
          });
      }
    },
  }
</script>
<style scoped>
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
.column {
  width: 33.3%;
  margin-bottom: 16px;
  padding: 0 8px;
}
@media screen and (max-width: 500px) {
  .column {
    width: 100%;
    display: block;
  }
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
.container {
  padding: 0 16px;
}
.container::after, .row::after {
  content: "";
  clear: both;
  display: table;
}
.description {
  color: grey;
  font-family: Arial, sans-serif;
  font-size: 25px;
}
</style>



