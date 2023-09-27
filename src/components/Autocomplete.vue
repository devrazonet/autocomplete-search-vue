<script>
  export default {
    name: 'Inputcomplete',
    props: {
      items: {
        type: Array
      }
    },
    data() {
      return {
        keyword: ''
      }
    },
    computed: {
      results() {
        if (this.keyword === '')
          return false
        else {
          return this.items.filter(item => {
            return item.name.toLowerCase().includes(this.keyword.toLowerCase())
          })
        }
      }
    },
    methods: {
      clearInput(){
        this.keyword = ''
      }
    }
  }
</script>

<template>
  <div class="position-relative mb-5 d-grid" style="width:400px">
    <div class="position-relative w-100 align-items-center justify-content-between d-flex" style="height:69px;">
      <div class="index" style="width:22px;height:22px;margin-left:14px;">
        <slot name="icon">
          <svg
            data-v-8dab3068=""
            aria-hidden="true"
            focusable="false"
            data-prefix="fal"
            data-icon="search"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512 512"
          ><path
            data-v-8dab3068=""
            fill="#c8c8c8"
            d="M508.5 481.6l-129-129c-2.3-2.3-5.3-3.5-8.5-3.5h-10.3C395 312 416 262.5 416 208 416 93.1 322.9 0 208 0S0 93.1 0 208s93.1 208 208 208c54.5 0 104-21 141.1-55.2V371c0 3.2 1.3 6.2 3.5 8.5l129 129c4.7 4.7 12.3 4.7 17 0l9.9-9.9c4.7-4.7 4.7-12.3 0-17zM208 384c-97.3 0-176-78.7-176-176S110.7 32 208 32s176 78.7 176 176-78.7 176-176 176z"
            class=""
          /></svg>
        </slot>
      </div>

      <input
        type="text" 
        class="py-4 px-5 w-100 rounded border-line position-absolute top-0 left-0" style="line-height:100%"
        v-model="keyword"/>

      <button
        type="button"
        class="index border-0"
        @click="clearInput"
        v-show="keyword.length"
        style="margin-right:14px;background:none;width:22px;height:22px;"
      >
        <svg
          class="h-2 w-2"
          stroke="#c8c8c8"
          fill="none"
          viewBox="0 0 8 8"
        >
          <path
              stroke-linecap="round"
              stroke-width="1.5"
              d="M1 1l6 6m0-6L1 7"
          />
        </svg>
      </button>
    </div>
    <div v-show="results.length">
      <ul class="shadow p-0 mb-5 bg-body-tertiary rounded-bottom" style="list-style: none;max-height:240px;overflow-y:auto;">
        <li v-for="(item, index) in results" :key="index" class="w-100 p-3 select-item">
          <a href="" class="text-secondary text-decoration-none d-flex">{{ item.name }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
  .border-line{
    border:1px solid #ddd;
  }
  .index{
    position:relative;
    z-index:2;
  }

  .select-item{
    text-align:left;
    border-bottom:2px solid transparent;
    transition: 0.2s all
  }
  .select-item:hover{
    padding-left:10px;
  }
  .select-item:hover{
    background:#eee;
    padding-left:1.5rem !important;
  }
  .select-item:hover a{
    color:#333 !important;
  }
</style>
