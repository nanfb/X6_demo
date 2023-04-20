<template>
  <div style="display:flex">
    <div class="layOut">
      <layout @cloneNodeMove="cloneNodeMove" @cloneNodeUp="cloneNodeUp"></layout>
    </div>
    <div @mouseover="containerOver($event, true)" @mouseout="containerOver($event, false)" id="container">


    </div>
    <!-- 功能区 -->
    <div class="action_list">
      <!-- <actionButton @action="handleAction"></actionButton> -->
    </div>
    <!-- 节点调整区 -->
    <div>
      <NodeAdjustment :graph="graph" ref="NodeAdjustment"></NodeAdjustment>
    </div>
  </div>
</template>
<script>
import { Graph, Node } from "@antv/x6";
import layout from "./layout";
import actionButton from "./ActionButton";
import NodeAdjustment from "./NodeAdjustment";
export default {
  name: "HelloWorld",
  components: {
    layout,
    actionButton,
    NodeAdjustment
  },
  data() {
    return {
      // 节点
      nodes: [
        {
          id: "node1", // String，可选，节点的唯一标识
          x: 10, // Number，必选，节点位置的 x 值
          y: 10, // Number，必选，节点位置的 y 值
          width: 80, // Number，可选，节点大小的 width 值
          height: 40, // Number，可选，节点大小的 height 值
          label: "111", // String，节点标签
        },
        {
          id: "node2",
          x: 100,
          y: 100,
          width: 80,
          height: 40,
          label: "222",
        },
      ],
      // line
      edges: [
        {
          source: "node1", // String，必须，起始节点 id
          target: "node2", // String，必须，目标节点 id
        },
      ],
      containerEvent: {
        containerMove: this.containerMove,
        nodeClick: this.nodeClick,
        containerscale: this.containerscale,
      },
      graph: {}, //画布
      isEnter: false, //是否进入画布
      cloneNodeSite: [],//克隆节点的位置
      NodeSelect: [],//节点选择器
      nodeAttr: {}, //节点样式
      transform: [],
      containerTranslate: { tx: 0, ty: 0 }//画布移动距离
    };

  },
  methods: {
    // 初始化节点
    createGraph() {
      this.graph = new Graph({
        container: document.getElementById("container"),
        // width: 800,
        // height: 600,
        panning: {
          enabled: true,
        },
        // 自动吸附
        connecting: {
          snap: true,
        },
        //节点大小可修改
        resizing: {
          enabled: true, 
        },
        // 这个东西涉及到元素拖入时的大小，后续优化--
        // mousewheel: true, //禁止画布放大缩小
        grid: {
          visible: true,
          size: 10,
        },
        background: {
          color: "#f0f0f0", // 设置画布背景颜色
        },

      });
      this.graph.fromJSON({
        nodes: this.nodes,
        edges: this.edges,
      });
      Graph.registerNode(
        "custom-node",
        {
          markup: [
            {
              tagName: "rect",
              groupSelector: "left",
              attrs: {
                x: 424,
                y: 119.4,
                width: 9,
                height: 19.2,
                transform: "translate(557.5 -299.5) rotate(90)",
              },
            },
            {
              tagName: "rect",
              groupSelector: "center",
              attrs: {
                x: 431.8,
                y: 127.8,
                width: 15,
                height: 2.4,
                transform: "translate(568.3 -310.3) rotate(90)",
              },
            },
            {
              tagName: "rect",
              groupSelector: "right",
              attrs: {
                x: 410.2,
                y: 127.8,
                width: 15,
                height: 2.4,
                transform: "translate(546.7 -288.7) rotate(90)",
              },
            },
          ],
          attrs: {
            left: {
              fill: "#730000",
            },
            center: {
              fill: "#730000",
            },
            right: {
              fill: "#730000",
            },
          },
        },
        true
      );
      // 添加节点
      this.graph.addNode({
        x: 0,
        y: 0,
        shape: "custom-node",
      });
    },
    containerOver(e, flag) {
      this.isEnter = flag;
    },

    // 事件
    cloneNodeMove(...arg) {
      this.cloneNodeSite = arg;
    },

    cloneNodeUp(cloneNode) {
      if (this.isEnter) {
        this.NodeSelect = []
        this.nodeAttr = {}
        // 父节点位移信息
        let reg = /[-+]?[0-9]*\.?[0-9]+/g //提取数字
        this.transform = cloneNode.getAttribute('transform').match(reg)
        let newNode = this.clearAttribute(cloneNode)
        // 创建节点
        this.createNode(newNode);

      }
    },
    // 获取节点属性
    getClondeNodeAttributes(cloneNode) {
      let getAttrs = (node) => {
        let attrs = {}
        for (let item of (node.attributes)) {
          attrs[item.name] = item.value
        }
        attrs.transform = 'translate(0, 0)'
        // node.tagName === 'text' ? attrs.text = node.textContent : '' // 文本节点处理 (文本位置处理作为参数设置，不设置默认节点处理，默认svg文本位置不好设置)
        this.nodeAttr[node.tagName] = attrs
        let NodeSelect = {
          tagName: node.tagName,
          groupSelector: node.tagName,
        }
        return NodeSelect
      }

      if (cloneNode.hasChildNodes()) {
        for (let node of cloneNode.childNodes) {
          node.tagName === 'g' ? this.getClondeNodeAttributes(cloneNode.children) : ''
          this.NodeSelect.push(getAttrs(node))
        }
      } else {
        cloneNode.tagName === 'g' ? this.getClondeNodeAttributes(cloneNode.children) : ''
        this.NodeSelect.push(getAttrs(cloneNode))
      }
    },

    createNode(cloneNode) {
      this.getClondeNodeAttributes(cloneNode)
      let node = new Node({
        width: 100,
        height: 100,
        shape: "vue-shape",
        x: this.transform[0] - 303 - this.containerTranslate.tx,
        y: this.transform[1] - this.containerTranslate.ty,
        markup: this.NodeSelect,
        attrs: this.nodeAttr,
      });
      this.graph.addNode(node);
    },
    // 清除不必要的属性
    clearAttribute(node) {
      return node
    },
    // 按钮处理
    handleAction(type) { },
    // 画布事件监听
    containerMove({ tx, ty }) {
      this.containerTranslate = { tx, ty }
    },
    containerscale({ sx, sy, ox, oy }) {
      this.containerTranslate = { sx, sy }
    },
    // 清除其他节点样式
    resetNodeStyel() {

    },
    // 节点点击事件
    nodeClick({ e, x, y, node, view }) {
      this.$refs.NodeAdjustment.init(node)
      // node.attr('rect/stroke', 'orange')
    }
  },

  mounted() {
    this.createGraph();
    // 画布事件注册
    this.graph.on("translate", this.containerEvent.containerMove); //监听画布移动
    this.graph.on('scale', this.containerEvent.containerscale) //监听画布缩放
    this.graph.on('node:click', this.containerEvent.nodeClick) //节点点击
  },
};
</script>
<style lang="less" scoped>
.layOut {
  height: 100vh;
  width: 16%;
  overflow: hidden;
  background-color: rgb(45, 175, 211);
}

#container {
  width: 100%;
  height: 100vh;
  flex: 1;
  background-color: rgb(243, 84, 84);
  z-index: 1;
  position: relative;
}

.action_list {
  position: fixed;
  top: 10px;
  left: calc(16% + 10px);
  z-index: 99;
}
</style>
