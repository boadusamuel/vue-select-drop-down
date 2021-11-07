<template>
  <div class="col-lg-12">
    <table
      class="table table-borderless"
      :class="{ 'table-bottom-margin': removeBottomMargin }"
      :removeBottomMargin="removeBottomMargin"
    >
      <thead>
        <tr>
          <slot name="headComponent"></slot>
        </tr>
      </thead>
      <tbody>
        <slot name="bodyComponent"></slot>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'zTable',
  props: {
    resultCount: {
      type: String,
      default: '',
    },
    removeBottomMargin: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style scoped>
.table-bottom-margin {
  margin-bottom: 4px;
}

.table-borderless td, .table-borderless th {
  border: 0 !important;
}

.table-borderless th {
  color: #23414e;
  font-family: 'Sora';
  font-style: normal;
  font-weight: 700;
  font-size: 12px;
  height: 17px;
}
</style>
