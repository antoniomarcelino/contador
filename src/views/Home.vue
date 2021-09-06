<template>
    <div   >
        <Counter 
          :year="2021"
          :month="8"
          :day="10"
          :hour="16"
          :minute="45"
          :second="10"
          :millisecond="10"
        />
    </div>
</template>

<script>
import Counter from '@/components/Counter.vue'

export default {
    components: {
        Counter,
    },
}
</script>