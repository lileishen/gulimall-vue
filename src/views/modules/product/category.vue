<template>
  <div>
    <el-tree
      :data="menus"
      :props="menuProps"
      show-checkbox
      node-key="id"
      default-expand-all
      :expand-on-click-node="false">
      <span class="custom-tree-node" slot-scope="{ node, data }">
        <span>{{ node.label }}</span>
        <span>
          <el-button
            type="text"
            size="mini"
            @click="() => appendMenu(data)">
            添加
          </el-button>
          <el-button
            type="text"
            size="mini"
            @click="() => removeMenu(node, data)">
            删除
          </el-button>
        </span>
      </span>
    </el-tree>
  </div>
</template>

<script>
// 这里可以导入其他文件 例如：组件、工具js、第三方插件js,json文件、图片文件等
// eg: import 《组件名称》 from '《文件路径》'

export default {
  // import 引入的组件需要注入到对象中才能使用
  components: {},
  props: {},
  // 这里用于存放数据
  data () {
    return {
      menus: null,
      menuProps: {
        children: 'children',
        label: 'name'
      }
    }
  },
//  计算属性 类似于data概念
  computed: {},
//  监控data 中数据变化
  watch: {},
//  方法集合
  methods: {
    handleNodeClick (data) {
      console.log(data)
    },
    getMenus () {
      this.$http({
        url: this.$http.adornUrl('/product/category/list/tree'),
        method: 'get'
      }).then(({data}) => {
        console.log(data)
        this.menus = data.data
      })
    },
    appendMenu (data) {
      console.log('添加')
    },

    removeMenu (node, data) {
      console.log('删除')
    }
  },
//  生命周期 -创建完成（可以访问当前this 实例）
  created () {
    this.getMenus()
  },
//  生命周期 - 挂载完成（可以访问Dom元素）
  mounted () {
  },
//  生命周期 - 创建之前
  beforeCreate () {
  },
//  生命周期 - 挂载之前
  beforeMount () {
  },
//  生命周期 - 更新之前
  beforeUpdate () {
  },
//  生命周期 - 更新之后
  updated () {
  },
//  生命周期 - 销毁之前
  beforeDestroy () {
  },
//  生命周期 - 销毁完成
  destroyed () {
  },
// 如果页面有keep-alive 缓存功能，这个函数会触发
  activated () {
  }

}
</script>

<style scoped>

</style>
