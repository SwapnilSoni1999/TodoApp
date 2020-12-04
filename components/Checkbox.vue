<template>
  <label class="inline-flex items-center justify-center">
    <input
      @click="check"
      type="checkbox"
      class="hidden absolute"
      name=""
      id=""
    />
    <span
      class="h-6 w-6 rounded-full checkbhox"
      :class="isChecked ? 'checked' : 'border-2'"
    >
      <img
        src="/images/icon-check.svg"
        :class="isChecked ? null : 'hidden'"
        alt=""
      />
    </span>
    <slot></slot>
    
  </label>
</template>

<script>
export default {
    data: () => ({
        isChecked: false
    }),
    props: {
        checkedStats: { type: Boolean }
    },
    methods: {
        check() {
            this.isChecked = !this.isChecked
            this.$emit('checked', this.isChecked)  
        }
    },
    created() {
        this.isChecked = this.checkedStats
    }
};
</script>

<style>
.checkbhox {
  cursor: pointer;
}

.checked {
  position: relative;  
}

.checked > img {
  position: absolute;
  top: 8px;
  right: 6px;
  pointer-events: none;
}

.checked::after {
  content: '';
  background: linear-gradient(45deg, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
  display: inline-block;
  @apply rounded-full h-6 w-6 border-2;
}

</style>