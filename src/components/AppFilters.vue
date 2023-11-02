<template>
  <aside class="app-filters">
    <section class="toggle-group">
      <button 
      class="button"
      v-for="filter in filters" :key="filter" 
      :class="{ 'button--primary': selectedFilter === filter }"
      @click="selectFilter(filter)">{{
        filter }}</button>
    </section>
  </aside>
</template>
<script lang="ts">
import { FilterType } from '@/models/FilterType';
import { PropType, defineComponent } from 'vue';

interface State {
  filters: FilterType[]
}

export default defineComponent({
  props: {
    selectedFilter: {
      type: String as PropType<FilterType>,
      required: true
    }
  },
  data(): State {
    return {
      filters: [
        FilterType.All,
        FilterType.Active,
        FilterType.Done
      ]
    }
  },
  methods: {
    selectFilter(filter: FilterType){
     this.$emit('selectFilter', filter);
      
    }
  },
  emits: {
    selectFilter: (filter: FilterType)=> filter
  }
})
</script>