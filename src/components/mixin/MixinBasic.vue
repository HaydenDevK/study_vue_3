<template>
  <h1>21. Mixin</h1>
  <ProductStatus />
  <FeeStatus />
  <SavingStatus />
  <!--
   - 예시처럼 3개 컴포넌트가 똑같이 생긴 data, methods 등을 각각 가지고 있을 때 mixin 사용 방법
    => 
    1. src/mixins/moneyMixin.js
    export default { 
        methods: {
            // 여기에 재사룡할  함수 정의
        } 
    } 
    2. 믹스인 함수가 필요한 component에 mixins 추가
    import addMoneyMixin from '../../mixins/moneyMixins'

    mixins: [
        addMoneyMixin
    ]

    - mixin data 생성 시, 각각 이름이 같을 뿐 각각의 컴포넌트의 data로 생성된다.
    즉, mixin은 똑같은 data를 한번 작성해서 여러개 만들어내는 생성자함수 같은 아인지? 아니면 하나의 

    - 프로젝트가 고도화될 수록 오히려 mixin을 파악하기 어려워질 수 있기 때문에, 최대한 간결하고 제한적이고 명료하게 사용해야 한다.
    Vue 3에서는 이런 문제를 해결하고자 Composition api 라는 것을 도입했다.
  -->
</template>

<script>
import ProductStatus from '@/components/mixin/ProductStatus';
import FeeStatus from '@/components/mixin/FeeStatus';
import SavingStatus from '@/components/mixin/SavingStatus';

export default {
  name: 'MixinBasic',
  components: {
    ProductStatus,
    FeeStatus,
    SavingStatus
  }
};
</script>
