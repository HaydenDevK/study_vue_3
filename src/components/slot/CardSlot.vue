<template>
  <div class="card">
    <div>Card</div>
    <div class="card-header">
      <slot name="header"></slot>
    </div>
    <div class="card-body">
      <slot name="body"></slot>
    </div>
    <div class="card-footer">
      <slot name="footer"></slot>
    </div>
    <div class="card-default">
      <slot></slot>
    </div>
    <slot>
      default string
      <!-- name이 없는 slot
          부모 컴포넌트에서 slot에 아무것도 안보낼 때 : default string
          부모 컴포넌트에서 v-slot:default로 내용을 보냈을 때 : 해당 내용
      -->
    </slot>
  </div>
</template>

<script>
export default {
  name: 'CardSlot'
};
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.3);
  padding: 1rem;
  margin-bottom: 1rem;
  width: 200px;
}
.card-header {
  color: red;
}
.card-body {
  color: green;
}
.card-footer {
  color: blue;
}
.card-default {
  color: gray;
}
</style>
