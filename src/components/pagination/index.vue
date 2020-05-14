<template>
    <!-- 分页组件 -->
    <div class="pagination">
        <!-- 左侧：展示数据条数 -->
        <div class="left-area">共{{ arrTotal }}条</div>
        <div class="prev" v-html="'<'" @click="pageUp"></div>
        <!-- 中间：分页选项卡 -->
        <div class="middle-area">
            <ul>
                <li
                    v-for="(item, index) in pagesList"
                    :key="'page' + index"
                    :class="item == newCurrentPage ? 'active' : ''"
                    @click="pageChange(item)"
                >
                    {{ item }}
                </li>
            </ul>
        </div>
        <div class="next" v-html="'>'" @click="pageDown"></div>
    </div>
</template>

<script>
export default {
    name: 'pagination',
    props: ['total', 'currentPage', 'size'],
    data() {
        return {
            newSize: 3, // 每页条数
            pagesList: [], // 分页选项卡列表
            newCurrentPage: 1,
        }
    },
    computed: {
        arrTotal() {
            return this.total
        },
    },

    created() {
        this.newSize = this.size
        this.newCurrentPage = this.currentPage
        this.getPageList()
    },
    watch: {
        currentPage() {
            this.newCurrentPage = this.currentPage
        },
    },
    updated() {},
    methods: {
        // 计算 分页选项卡列表数据
        getPageList(total) {
            total = total || this.arrTotal
            let pageSize = total / this.size // 共多少页
            console.log(total)
            if (Number(total) < Number(this.newSize)) {
                this.pagesList = [1]
            } else {
                // 生成1~num的自然数，赋值给pagesList
                this.pagesList = []
                if (total % this.newSize !== 0) {
                    pageSize = Math.floor(pageSize) + 1
                }
                for (let i = 0; i < pageSize; i++) {
                    this.pagesList.push(i + 1)
                }
            }
        },
        pageUp() {
            this.newCurrentPage > 1 && this.newCurrentPage--
            this.$emit('current-change', this.newCurrentPage)
        },
        // 从分页选项卡中 跳转到指定页
        pageChange(item) {
            this.$emit('current-change', item)
            this.newCurrentPage = item
        },
        pageDown() {
            console.log(this.newCurrentPage)
            this.newCurrentPage < this.arrTotal / this.size && this.newCurrentPage++
            this.$emit('current-change', this.newCurrentPage)
        },
    },
}
</script>

<style lang="scss" src="./index.scss" scoped></style>
