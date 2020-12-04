<template>
  <div class="border-b-2 w-full p-4 todoo">
    <GradCheckbox @checked="check" :isChecked="checkedStats">
      <span
        class="px-2"
        :class="isChecked ? 'line-through text-gray-500' : 'text-gray-700'"
      >
        {{ todoText }}
      </span>
      
    </GradCheckbox>
  </div>
</template>

<script>
import GradCheckbox from "~/components/Checkbox";
export default {
  data: () => ({
    isChecked: false,
  }),
  props: {
      todoText: { type: String, required: true },
      checkedStats: { type: Boolean, required: true },

  },
  methods: {
    check(isChecked) {

      this.isChecked = isChecked;
    },
  },
  created() {
      this.isChecked = this.checkedStats
  },
  components: {
    GradCheckbox,
  },
};
</script>

<style>
.todoo:last-child {
    border-bottom: none;
}
</style>