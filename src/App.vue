<template>
  <span></span>
</template>
<script>
import AREA from '@/assets/area.js'

export default {
  mounted() {
    const arr = this.complie(AREA)
    console.log(arr)
  },
  methods: {
    complie(data) {
      const _arr = []
      const arr = []
      data.map(item => {
        // big_area 字段去重
        (_arr.indexOf(item['big_area']) < 0) && _arr.push(item['big_area'])
      })
      _arr.map((item, i) => {
        // 让数据结构变得工整
        arr[i] = {
          label: item,
          data: []
        }
        data.map(key => {
          (item === key['big_area']) && arr[i].data.push({ name: key['name'], city: key['city'] })
        })
      })

      const resetName = (data) => {
        // 递归重新设置key
        const arr = []
        data.map(item => {
          if (typeof (item) === 'string') {
            // 已经递归到最后一层，数组里的每一个元素都是字符串
            arr.push({ label: item, children: [] })
          } else {
            // 元素其中有一项是字符串，另一项则是数组
            const obj = {
              label: '',
              children: []
            }
            for (let key in item) {
              if (typeof (item[key]) === 'string') {
                // 字符串归入 label
                obj['label'] = item[key]
              } else {
                // 数组则使用递归，并归入children
                obj['children'] = resetName(item[key])
              }
            }
            arr.push(obj)
          }
        })
        return arr
      }
      return resetName(arr)
    }
  }
}
</script>

