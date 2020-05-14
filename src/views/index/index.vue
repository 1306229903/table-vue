<template>
    <div>
        <p>table-vue</p>
        <table-vue :data="list" :columns="columns"></table-vue>
    </div>
</template>
<script>
import tableVue from '@/components/table/table'

export default {
    components: {tableVue},
    data() {
        return {
            //配置对应的设置项，来表示代表有无设置项，如hasSort代表排序，hasFilter代表过滤
            columns: [
                {
                    // table表头：colName-表头展示的中文名；field - 对应的数据字段
                    colName: '姓名',
                    field: 'name',
                    hasSort: true,
                },
                {
                    colName: '性别',
                    field: 'sex',
                    hasFilter: true,
                },
                {
                    colName: '年龄',
                    field: 'age',
                    hasSort: true,
                },
                {
                    colName: '身高',
                    field: 'height',
                },
                {
                    colName: '体重',
                    field: 'weight',
                    hasFilter: true,
                },
                {
                    colName: '住址',
                    field: 'address',
                },
            ],
            list: [], // table列表数据
        }
    },
    created() {
        this.getDataList()
    },
    methods: {
        // 请求列表数据：配合后台
        getDataList() {
            this.list = [
                {
                    id: 101,
                    name: '测试1',
                    sex: '女',
                    age: 18,
                    height: '160',
                    weight: '48',
                    address: '都是发的说法',
                },
                {
                    id: 102,
                    name: '测试2',
                    sex: '男',
                    age: 28,
                    height: '187',
                    weight: '70',
                    address: '大师法第三方',
                },
                {
                    id: 103,
                    name: '测试3',
                    sex: '男',
                    age: 18,
                    height: '187',
                    weight: '80',
                    address: '大沙发垫付',
                },
                {
                    id: 104,
                    name: '测试4',
                    sex: '女',
                    age: 23,
                    height: '160',
                    weight: '48',
                    address: '俺的沙发上',
                },
                {
                    id: 105,
                    name: '测试5',
                    sex: '男',
                    age: 1,
                    height: '187',
                    weight: '70',
                    address: '大师傅',
                },
                {
                    id: 106,
                    name: '测试6',
                    sex: '男',
                    age: 8,
                    height: '187',
                    weight: '80',
                    address: '大师发大水发多少',
                },
                {
                    id: 107,
                    name: '测试7',
                    sex: '男',
                    age: 8,
                    height: '187',
                    weight: '80',
                    address: '阿斯顿发的说法',
                },
                {
                    id: 108,
                    name: '测试8',
                    sex: '男',
                    age: 8,
                    height: '187',
                    weight: '80',
                    address: '大师傅大师傅',
                },
                {
                    id: 109,
                    name: '测试9',
                    sex: '男',
                    age: 8,
                    height: '187',
                    weight: '80',
                    address: '大师法都是',
                },
                {
                    id: 110,
                    name: '测试10',
                    sex: '男',
                    age: 8,
                    height: '187',
                    weight: '80',
                    address: '维范德萨发的吾尔',
                },
            ]
    
        },
    },
}
</script>
