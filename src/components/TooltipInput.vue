<template>
  <div class="tooltip-box">
    <span class="close-icon" @click="closeEditor">X</span>
    <button type="button" @click="changeStyle('bold')" class="btn btn-bold">B</button>
    <button type="button" @click="changeStyle('italic')" class="btn btn-italic">I</button>
    <button type="button" @click="changeStyle('underline')" class="btn btn-underline">U</button>
    <textarea type="text" v-model="newText" @input="updateText"/>
  </div>
</template>

<script>
export default {
  name: 'TooltipInput',
  props: ['currentText'],
  data() {
    return {
      newText: this.currentText
    }
  },
  methods: {
    updateText: function() {
      this.$emit('updatedText', this.newText)
    },
    closeEditor: function() {
      this.$emit('closeEditor', true)
    },
    changeStyle: function(style) {
      this.$emit('changeStyle', style)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .tooltip-box {
    position: relative;
    display: inline-block;
    background-color: var(--violet);
    padding: .5rem 1rem;
    width: auto;
    margin: auto;
    border-radius: 3px;
    textarea {
      width: 250px;
      height: 50px;
      padding: .5rem;
      border-radius: 3px;
      border: 3px solid var(--pink);
      &:focus {
        outline: none;
      }
    }
    .close-icon {
      position: relative;
      display: block;
      width: 10px;
      padding: 2px 4px;
      left: 96%;
      top: -4px;
      font-weight: bold;
      cursor: pointer;
    }
    .btn {
      display: inline-block;
      background-color: var(--dirty-orange);
      border: none;
      border: 1px solid var(--light-pink);
      margin: 3px;
      cursor: pointer;
      &-bold {
        font-weight: bold;
      }
      &-italic {
        font-style: italic;
      }
      &-underline {
        text-decoration: underline;
      }
    }
  }
</style>
