<template>
  <div class="container">
    <transition name="pop-up">
      <tooltip-input
      class="tooltip"
      v-bind:currentText="text"
      @updatedText="changeText"
      @closeEditor="closeTooltip"
      @changeStyle="updateStyle"
      @changeTextColor="updateTextColor"
      v-if="showEditor"/>
    </transition>
    <p class="editable-text"
    v-on:click="editText"
    v-bind:style="{color: textColor}"
    v-bind:class="{
      bold: styles.bold,
      italic: styles.italic,
      underline: styles.underline
    }">
      {{ text }}
    </p>
  </div>
</template>

<script>
import TooltipInput from '@/components/TooltipInput.vue'

export default {
  name: 'Article',
  components: {
    'tooltip-input': TooltipInput
  },
  data() {
    return {
      text: 'Some basic text.Click to edit!',
      showEditor: false,
      textColor: '',
      styles: {
        bold: false,
        italic: false,
        underline: false
      }
    }
  },
  methods: {
    editText: function() {
      this.showEditor = true
    },
    changeText: function(val) {
      this.text = val
    },
    closeTooltip: function(val) {
      this.showEditor = false
    },
    updateStyle: function(style) {
      this.styles[style] = !this.styles[style]
    },
    updateTextColor: function(color) {
      this.textColor = color
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .container {
    position: relative;
    width: 100%;
    max-width: 1200px;
    margin: 3rem auto;
  }

  .editable-text {
    font-size: 2rem;
    color: #555;
    transition: color linear .3s;
    &.bold {
      font-weight: bold;
    }
    &.italic {
      font-style: italic;
    }
    &.underline {
      text-decoration: underline;
    }
  }

  .tooltip {
    transform: scale(1);
  }

  .pop-up {
    &-enter,
    &-leave-to {
      transform: scale(0);
    }
    &-enter-active,
    &-leave-active {
      transition: transform cubic-bezier(0.175, 0.885, 0.32, 1.15) .3s;
    }
  }
</style>
