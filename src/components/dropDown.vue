<template>
  <div
    v-if="shouldOpen"
    :style="{ width: dropDownWidth }"
    class="z-selector px-0 mt-3"
    :shouldOpen="shouldOpen"
    :setDropdownPlaceholder="setDropdownPlaceholder"
  >
    <div class="border-0 px-0">
      <div id="" class="card-body px-0 py-0">
        <div class="row p-0">
          <z-table :remove-bottom-margin="removeBottomMargin">
            <template #bodyComponent>
              <tr class="text-capitalize ml-3 default-font-12-600 mb-0 pt-0">
                <td class="pt-1 pl-3">{{ setDropdownPlaceholder }}</td>
              </tr>
              <tr
                v-for="(option, index) in options"
                :key="index"
                :v-if="options"
                class="text-justify"
                @click.prevent="handleDropDownSelected(option)"
              >
                <ztd
                  :data="option"
                  class="z-pointer pl-3 default-font-12-normal"
                />
              </tr>
              <tr
                v-for="(option, index) in arrayOfObjects"
                :key="index"
                :v-if="arrayOfObjects"
                class="text-justify"
                @click.prevent="handleDropDownSelected(option.externalId)"
              >
                <ztd
                  :data="option.name"
                  class="z-pointer pl-3 default-font-12-normal"
                />
              </tr>
            </template>
          </z-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import  zTable from './zTable.vue'

export default {
  name: 'DropDown',
  components: {zTable},
  props: {
    shouldOpen: {
      type: Boolean,
      default: false,
    },
    setDropdownPlaceholder: {
      type: String,
      default: '',
    },
    dropDownWidth: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default() {
        return []
      },
    },
    arrayOfObjects: {
      type: Array,
      default() {
        return []
      },
    },
    removeBottomMargin: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleDropDownSelected(data) {
      return this.$emit('selected', data)
    },
  },
}
</script>

<style scoped>
.z-selector {
  width: 350px;
  border-radius: 8px !important;
  background: #ffffff;
  z-index: 1;
  min-height: 20px;
  border: 1px solid #cbd4db;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.06);
  position: absolute;
  max-height: 267px !important;
  overflow-y: auto !important;
  overflow-x: hidden !important;
}

.z-pointer {
  cursor: pointer;
}

.z-pointer:hover {
  background: #f3f3f3;
}

table td {
  height: 37px !important;
}

table {
  margin: 0 !important;
}

.card-body {
  max-height: 267px !important;
}

.default-font-12-600 {
  font-family: Sora;
  font-style: normal;
  font-weight: 600;
  font-size: 12px;
  line-height: 140%;
}

.default-font-12-normal {
  font-family: Sora;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 140%;
}
</style>
