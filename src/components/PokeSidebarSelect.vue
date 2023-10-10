<template>
  <div class="mb-4">
    <p>{{ label }}:</p>
    <div :class="[isGameStart ? 'cursor-not-allowed' : 'cursor-pointer']" class="">
      <template v-for="(item, index) in options" :key="index">
        <PokeSidebarSelectItem
          class="w-full"
          :class="{ hidden: isGameStart && optionSelected !== item }"
          :isActive="optionSelected === item"
          :content="item"
          @click="changeOption(item)" />
      </template>
    </div>
  </div>
</template>

<script setup>
  import PokeSidebarSelectItem from './PokeSidebarSelectItem.vue'
  const emit = defineEmits(['change'])
  const props = defineProps({
    optionSelected: [String, Number],
    options: Array,
    isGameStart: Boolean,
    label: String,
  })
  const changeOption = (option) => {
    if (!props.isGameStart) {
      emit('change', option)
    }
  }
</script>
