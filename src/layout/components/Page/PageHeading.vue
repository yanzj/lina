<template>
  <div class="page-heading">
    <el-row :gutter="0">
      <el-col :span="16" class="page-heading-left">
        <slot><h2>{{ title }}</h2></slot>
      </el-col>
      <el-col :span="8">
        <div class="page-heading-right">
          <slot name="rightSide" />
        </div>
      </el-col>
    </el-row>
  </div>
<!--    <Breadcrumb />-->
</template>

<script>
export default {
  name: 'PageHeading',
  props: {
    title: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
  .page-heading {
    border-top: 0;
    padding: 15px 30px 15px 25px;
    background-color: #ffffff;
    min-height: 1px;
  }

  .page-heading-left, h2 {
    font-size: 18px;
    font-weight: 300;
    line-height: 1.5;
    /*margin-bottom: 12px;*/
    height: 30px;
    max-height: 32px;
  }

  .page-heading-right {
    float: right;
  }
</style>
