<template>
  <h1>2. Attr Binding :</h1>
  <div id="title"></div>
  <div v-bind:id="dynamicId">dynamic attr binding</div>
  <a v-bind:href="dynamicUrl">naver</a>
  <img v-bind:src="img.dynamicSrc" v-bind:alt="img.dynamicAlt" />
  <input v-bind:type="dynamicType" />
  <div v-bind:style="dynamicStyle1">동적 스타일 바인딩</div>
  <div
    v-bind:style="{
      color: `${dynamicStyle2.color}`,
      fontSize: `${dynamicStyle2.size}`
    }"
  >
    동적 스타일 바인딩2
  </div>
  <div v-bind:style="[dynamicStyle3, dynamicStyle4]">
    동적 스타일 바인딩3 (배열)
  </div>
</template>

<script>
export default {
  name: 'BindingAttr',
  data() {
    return {
      dynamicId: 'title',
      dynamicUrl: 'https:www.naver.com',
      img: {
        dynamicSrc: 'https://placeimg.com/100/100/any',
        dynamicAlt: 'random'
      },
      dynamicType: 'range',
      dynamicStyle1: 'color: red; font-size: 24px;',
      dynamicStyle2: {
        color: 'blue',
        size: '18px'
      },
      dynamicStyle3: {
        color: 'pink'
      },
      dynamicStyle4: {
        'font-weight': 'bold'
      }
    };
  }
};
</script>

<style scoped>
#title {
  color: red;
  background: yellow;
}
#content {
  color: blue;
  background: pink;
}
</style>
