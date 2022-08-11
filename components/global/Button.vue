<template>
  <Button :is="type" :href="href" class="button">
    <slot></slot>
    
  </Button>
</template>

<script>
import axios from 'axios'

  export default {
    props: {
      href: {
        type: String,
        default: null
      },
      to: {
        type: String,
        default: null
      }
    },
    computed: {
      type() {
        if (this.href) {
          return 'a'
        } else {
          return 'button'
        }
      }
    },
    async sendRequest(id){
      const res = await axios.patch(id);
      res.data.headers['Content-Type']; //application/json;charset=utf-8
      return{
        res
      }
    }
  }
</script>

<style scoped>
  .button {
    display: inline-flex;
    margin: 5px;
    padding: 10px;
    background: #fff;
    border: 2px solid var(--border-color);
    border-radius: 3px;
    color: var(--border-color);
    font-family: "Quicksand", sans-serif;
    font-size: 1em;
    font-weight: 700;
    letter-spacing: 0.02em;
    line-height: 1;
    text-decoration: none;
    cursor: pointer;
    transition: 0.3s;
    width: 200px;
    text-align: center;
  }

  .button:hover {
    background: var(--border-color);
    color: #fff;
  }
</style>