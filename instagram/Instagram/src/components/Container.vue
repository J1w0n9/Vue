//Container.vue

<template>
  <div class="container">
    <!-- 리스트 페이지 -->
    <div v-if="step == 0">
      <Post v-for="(post, index) in posts" :key="index" :post="post" />
    </div>

    <!-- 필터 선택 페이지 -->
    <div v-if="step == 1">
      <!-- 선택한 필터 미리보기 -->
      <div
        class="upload-image"
        :class="선택한필터"
        :style="{ backgroundImage: `url(${image})` }"
      ></div>

      <div class="filters">
        <FilterBox
          :image="image"
          v-for="(filter, index) in 필터들"
          :key="index"
          :filter="filter"
        />
      </div>
    </div>

    <!-- 글 작성 페이지 -->
    <div v-if="step == 2">
      <div
        class="upload-image"
        :class="선택한필터"
        :style="{ backgroundImage: `url(${image})` }"
      ></div>
      <div class="write">
        <textarea
          class="write-box"
          @input="writeText($event.target.value)"
        >write!</textarea>
      </div>
    </div>
  </div>
</template>

<script>
import Post from './Post.vue';
import FilterBox from './Filterbox.vue';

export default {
  name: 'Container',
  components: {
    Post,
    FilterBox,
  },
  props: {
    step: Number,
    posts: Array,
    image: String,
  },
  data() {
    return {
      선택한필터: '',
      필터들: [
        'aden',
        '_1977',
        'brannan',
        'brooklyn',
        'clarendon',
        'earlybird',
        'gingham',
        'hudson',
        'inkwell',
        'kelvin',
        'lark',
        'lofi',
        'maven',
        'mayfair',
        'moon',
        'nashville',
        'perpetua',
        'reyes',
        'rise',
        'slumber',
        'stinson',
        'toaster',
        'valencia',
        'walden',
        'willow',
        'xpro2',
      ],
    };
  },
  mounted() {
    this.emitter.on('select-filter', (filter) => {
      this.선택한필터 = filter;
    });
  },
  methods: {
    writeText(text) {
      this.emitter.emit('write-text', text);
    },
  },
};
</script>