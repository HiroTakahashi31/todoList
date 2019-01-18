<template>
  <div>
    Formページ
    <HeadComp></HeadComp>
    <component :is="isComponent" ></component>
    <button @click="buttonAction">{{button}}</button>
  </div>
</template>

<script>
import HeadComp from '@/components/HeadComp'
import TextareaComp from '@/components/TextareaComp'
import StringComp from '@/components/StringComp'
import {mapActions, mapGetters} from 'vuex'

export default {
  name: 'form',
  methods: mapActions('Form', {
    'buttonAction': 'buttonAction'
  }),
  computed: mapGetters('Form', {
    'button': 'getButton',
    'isComponent': 'getComponent'
  }),
  components: {
    HeadComp,
    TextareaComp,
    StringComp
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@mixin flex-vender() {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
}
.task-list {
  @include flex-vender;
  flex-direction: column;
  align-items: center;
  &__item {
    width: 270px;
    text-align: left;
    $element: #{&};
    &--checked {
      @extend #{$element};
      color: #85a6c6;
    }
  }
}
</style>
