<template>
  <div class="tooltip-box">
    <span class="close-icon" @click="closeEditor">X</span>
    <div class="container-tools">
      <button type="button" @click="changeStyle('bold')" class="btn btn-bold" title="Bold">B</button>
      <button type="button" @click="changeStyle('italic')" class="btn btn-italic" title="italic">I</button>
      <button type="button" @click="changeStyle('underline')" class="btn btn-underline" title="underline">U</button>
      <input type="color" name="text-color" v-model="textColor" @input="changeTextColor" title="change color">
    </div>
    <textarea type="text" v-model="newText" @input="updateText"/>
  </div>
</template>

<script>
export default {
  name: 'TooltipInput',
  props: ['currentText'],
  data() {
    return {
      newText: this.currentText,
      textColor: ''
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
    },
    changeTextColor: function() {
      this.$emit('changeTextColor', this.textColor)
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
    .container-tools {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      width: 100px;
      margin: 0 auto 1rem;
    }
    .btn {
      display: inline-block;
      width: 26px;
      background-color: var(--dirty-orange);
      border: 1px solid var(--light-pink);
      border-radius: 3px;
      margin: 0 0 5px;
      font-size: 1rem;
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
    input[type=color] {
      width: 100%;
      cursor: pointer;
      border-radius: 3px;
    }
  }
</style>
