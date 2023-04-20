<template lang="">
    <div v-show="show" class="floatingPanel">
        节点类型：{{type}}
        <br>
        <button @click="createLinkPile">创建链接桩</button>
    </div>
</template>
<script>
export default {
    name: 'NodeAdjustment',
    data() {
        return {
            show: false,
            type: 'node',
            node: {}
        }
    },
    props: ['graph'],
    methods: {
        init(node) {
            this.show = true
            this.node = node
            // 清除其他样式
            console.log(node)
            this.reset()
            node.attr('rect/stroke', 'orange')
        },
        reset() {
            this.graph.drawBackground({ color: '#f0f0f0' })
            const nodes = this.graph.getNodes()
            // const edges = this.graph.getEdges()
            nodes.forEach((node) => {
                node.attr('rect/stroke', 'red')
            })
            // edges.forEach((edge) => {
            //     edge.attr('line/stroke', 'black')
            //     edge.prop('labels/0', {
            //         attrs: {
            //             body: {
            //                 stroke: 'black',
            //             },
            //         },
            //     })
            // })
        },
        createLinkPile() {

        }
    }
}
</script>
<style lang="less" scoped>
.floatingPanel {
    position: fixed;
    top: 30px;
    right: 70px;
    border-radius: 5px;
    box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.2);
    width: 300px;
    height: 300px;
    background: #fff;
    padding: 5px;
    z-index: 999;
}
</style>></style>