<template>
  <div style="display:flex">
    <div class="layOut">
      <layout dowg></layout>
    </div>
    <div @mouseover="containerOver($event,true)" @mouseout="containerOver($event,false)" id="container"></div>
  </div>
</template>
<script>
import { Graph } from "@antv/x6";
import { Addon } from "@antv/x6";
import layout from "./layout";
export default {
  name: "HelloWorld",
  components: {
    layout,
  },
  data() {
    return {
      // 节点
      nodes: [
        {
          id: "node1", // String，可选，节点的唯一标识
          x: 0, // Number，必选，节点位置的 x 值
          y: 0, // Number，必选，节点位置的 y 值
          width: 80, // Number，可选，节点大小的 width 值
          height: 40, // Number，可选，节点大小的 height 值
          label: "hello", // String，节点标签
        },
        {
          id: "node2",
          x: 100,
          y: 100,
          width: 80,
          height: 40,
          label: "zzz",
        },
      ],
      // 边
      edges: [
        // {
        //   source: "node1", // String，必须，起始节点 id
        // },
        {
          source: "node1", // String，必须，起始节点 id
          target: "node2", // String，必须，目标节点 id
        },
      ],
      graph: {}, //画布
    };
  },
  methods: {
    // 初始化节点
    createGraph() {
      this.graph = new Graph({
        container: document.getElementById("container"),
        // width: 800,
        // height: 600,
        panning: true,
        mousewheel: true,
        grid: true,
        background: {
          color: "#ccc", // 设置画布背景颜色
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
    containerOver(e, flag){
      console.log(flag)
      console.log("containerOver--划入");
    }
  },

  mounted() {
    this.createGraph();
  },
};
</script>
<style lang="less" scoped>
.layOut {
  height: 100vh;
  width: 16%;
  background-color: rgb(247, 113, 113);
}

#container {
  width: 100%;
  height: 100vh;
  flex: 1;
  background-color: rgb(255, 255, 255);
}
</style>
