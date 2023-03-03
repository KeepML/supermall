<template>
    <div class="tab-control">
        <div v-for="(item,index) in titles" 
             class="tab-control-item"
             :class="{active:index ===currentIndex}"
             @click="itemClick(index)">
            <span>{{ item }}</span>
        </div>
    </div>
</template>

<script>
    export default ({
        name:"TabControl",
        props: {
            titles: Array,
            default(){
                return []
            }
        },
        data(){
            return {
               currentIndex: 0 //记录当前选中的索引
            }
        },
        methods: {
            itemClick(index) {
                this.currentIndex = index;
            }
        }
    })
</script>

<style scoped>
    .tab-control {
        display: flex;
        text-align: center;
        font-size: 14px;
        height: 40px;
        line-height: 40px;
        background-color: #fff;
    }

    .tab-control-item {
        flex: 1;
    }
    .tab-control-item span {
        padding: 5px; /*设置文本和下划线距离 */
    }

    .active {
        color: var(--color-high-text); /*设置选中时字体颜色 */
    }

    .active span {
        border-bottom: 3px solid var(--color-tint);/*设置选中文本下划线颜色 */
    }
</style>