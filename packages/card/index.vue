<template>
  <div class="van-card" :class="{ 'van-card--center': centered }">
    <div class="van-card__thumb">
      <slot name="thumb">
        <img :src="thumb" class="van-card__img" >
      </slot>
    </div>
    <div class="van-card__content">
      <slot name="title">
        <div class="van-card__row" v-if="title || price !== undefined">
          <div v-if="title" class="van-card__title">{{ title }}</div>
          <div v-if="price !== undefined" class="van-card__price">{{ currency }} {{ price }}</div>
        </div>
      </slot>
      <slot name="desc">
        <div class="van-card__row" v-if="desc || num !== undefined">
          <div v-if="desc" class="van-card__desc">{{ desc }}</div>
          <div v-if="num !== undefined" class="van-card__num">x {{ num }}</div>
        </div>
      </slot>
      <slot name="tags" />
    </div>
    <div class="van-card__footer" v-if="$slots.footer">
      <slot name="footer" />
    </div>
  </div>
</template>

<script>
import create from '../utils/create';

export default create({
  name: 'card',

  props: {
    thumb: String,
    title: String,
    desc: String,
    centered: Boolean,
    num: [Number, String],
    price: [Number, String],
    currency: {
      type: String,
      default: '¥'
    }
  }
});
</script>
