<template>
  <div>
    <button
      class="
        form-control
        select-input
        default-font-12-normal
        z-black-color
        truncate
      "
      :style="{ width: setWidth }"
      @click.prevent="handleDropDownOptions"
      @blur="checkBlur"
    >
      {{ setPlaceholder }}
    </button>
    <dropDown
      :set-dropdown-placeholder="setDropdownPlaceholder"
      :should-open="shouldOpen"
      :options="options"
      :array-of-objects="arrayOfObjects"
      :remove-bottom-margin="removeBottomMargin"
      :drop-down-width="dropDownWidth"
      @selected="handleDropDownSelected"
    ></dropDown>
  </div>
</template>

<script>
import dropDown from './dropDown'


export default {
  name: 'ZSelect',
  components: { dropDown },
  props: {
    // Placeholder of input field
    setPlaceholder: {
      type: String,
      default: '',
    },
    // Set width of drop down list
    dropDownWidth: {
      type: String,
      default: '',
    },
    // Set width of select button
    setWidth: {
      type: String,
      default: '350px',
    },
    // Display or hide drop down list 
    shouldOpen: {
      type: Boolean,
      default: false,
    },
    // Placeholder for drop down
    setDropdownPlaceholder: {
      type: String,
      default: '',
    },
    // Items in array
    options: {
      type: Array,
      default() {
        return []
      },
    },
    // Items(object) in array
    arrayOfObjects: {
      type: Array,
      default() {
        return []
      },
    },
    // Removes bottom margin of drop down list
    removeBottomMargin: {
      type: Boolean,
      default: false,
    },
  },
  // Toggle drop down list
  methods: {
    handleDropDownOptions() {
      this.$emit('showDropDown')
    },
    // Hide drop down list when select button is not in focus
    checkBlur() {
      this.$emit('blur')
    },
    // Event emiited upon selection from drop down
    handleDropDownSelected(data) {
      return this.$emit('selected', data)
    },
  },
}
</script>

<style scoped>
.select-input {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  height: 50px;
  left: 0;
  top: 31px;
  border: 1px solid #cbd4db;
  box-sizing: border-box;
  border-radius: 10px;
}

.select-input:after {
  display: block;
  content: url('../assets/icons/carret.svg');
  width: 14px;
  height: 8px;
  padding-bottom: 10px;
  margin-left: 2px;
}

button.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
}

.z-black-color {
  color: #121212;
}
</style>
