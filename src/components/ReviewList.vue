<script setup>
defineProps({
  reviews: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <div class="review-container">
    <h3>
      <!-- from the parent-->
      <slot name="heading"></slot>
    </h3>
    <ul>
      <li v-for="(review, index) in reviews" :key="index">
        <!-- from the parent-->
        <slot name="item" :review="review">
          <!-- riga 21 e 22 vengono renderizzati nel caso in cui, in ProductDisplay, 
            non è definito il named template "item" -->
          <span>{{ review.name }}</span
          >: <span>{{ review.content }}</span>
        </slot>
      </li>
    </ul>
  </div>
</template>
