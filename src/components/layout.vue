<template>
    <div>
        <!-- 常用组件 -->
        <div v-for="item in comList" :key="item" class="default_com">
            <div class="default_title com_title">{{ item }}</div>
            <div class="default_content" @mousedown.prevent.capture="handleDown">
                <template v-if="item === '通用节点'">
                    <div v-for="item in 3" :key="item" class="default_item">
                        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <circle class="test" cx="45" cy="45" r="40" stroke="black" stroke-width="2" fill="red" />
                            <!-- <rect x="120" y="120" width="70" height="70" stroke="black" fill="green" stroke-width="5" /> -->
                        </svg>
                    </div>
                    <div class="default_item">
                        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <rect x="0" y="0" width="100" stroke="red" stroke-width="5" height="100" fill="#987281">
                            </rect>
                        </svg>
                    </div>
                </template>
                <template v-else>
                    <div class="default_item">
                        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <g>
                                <circle class="test" cx="50" cy="50" r="30" stroke="black" stroke-width="2"
                                    fill="rgba(0,0,0,0)" />
                                <rect x="22" y="22" width="20" height="20" stroke="black" fill="green" stroke-width="5" />
                            </g>
                        </svg>
                    </div>
                </template>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: "layout",
    data() {
        return {
            down: false,
            cloneNode: {},
            cloneSvg: {},
            x: 0,
            y: 0,
            left: 0,
            top: 0,
            comList: ['通用节点', '特殊节点']
        };
    },
    props: [],//传递画布的放大缩小倍率
    methods: {
        // 对于合并的g获取到svg
        getSvg(dom) {
            let svg = {}
            if (dom.tagName === 'svg') {
                svg = dom
            } else {
                svg = this.getSvg(dom.parentNode)
            }
            return svg
        },
        handleDown(e) { //使用事件代理来做
            this.down = true
            document.addEventListener('mousemove', this.handleMove)
            document.addEventListener('mouseup', this.handleUp)
            this.cloneSvg = document.querySelector('svg').cloneNode(false)
            this.cloneSvg.style.position = 'fixed'
            this.cloneSvg.style.top = '0px'
            this.cloneSvg.style.width = '100%'
            this.cloneSvg.style.height = '100vh'
            this.cloneSvg.style.zIndex = 99
            this.cloneSvg.style.pointerEvents = 'none' //很关键的一个属性
            const group = e.target.closest('g');
            if (group) { //对于合并g元素进行处理
                this.setPropertiesCloneNode(group, e)
            } else {
                this.setPropertiesCloneNode(e.target, e)
            }
        },
        setPropertiesCloneNode(node, e) {
            this.cloneNode = node.cloneNode(true)
            this.cloneNode.style.opacity = .5
            let svg = this.getSvg(node)
            this.left = e.target.getBoundingClientRect().left - svg.getBoundingClientRect().left
            this.top = e.target.getBoundingClientRect().top - svg.getBoundingClientRect().top
            this.cloneSvg.appendChild(this.cloneNode)
            document.body.appendChild(this.cloneSvg)
            this.getcoordinate(e)
        },
        // 计算偏移量
        getcoordinate(e) {
            this.x = e.clientX - (this.cloneNode.getBoundingClientRect().width / 2) - this.left
            this.y = e.clientY - (this.cloneNode.getBoundingClientRect().height / 2) - this.top
            this.cloneNode.setAttribute('transform', `translate(${this.x}, ${this.y})`); //比例
        },
        handleMove(e) {
            if (!this.down) return
            this.getcoordinate(e)
            this.$emit('cloneNodeMove', [e.clientX, e.clientY])
        },
        handleUp() {
            this.down = false
            this.cloneNode.removeAttribute('style')
            this.$emit('cloneNodeUp', this.cloneNode)
            this.reset()
        },
        reset() {
            this.cloneNode.removeEventListener('mousedown', this.handleDown)
            document.removeEventListener('mousemove', this.handleMove)
            document.removeEventListener('mouseup', this.handleUp)
            this.cloneSvg.remove()
            this.down = false
            this.cloneNode = {}
            this.cloneSvg = {}
            this.x = 0
            this.y = 0
            this.left = 0
            this.top = 0
        }
    },
    mounted() {

    }
};
</script>
<style lang="less" scoped>
/* 布局 */

.com_title {
    width: 100%;
    height: 30px;
    background-color: #5b5656;
    cursor: pointer;
    text-align: center;
    line-height: 30px;
    color: aquamarine;
}

.default_com {
    width: 100%;

    .default_content {
        padding: 10px;
        box-sizing: border-box;
        width: 100%;
        height: 300px;
        display: flex;
        flex-wrap: wrap;
        background-color: #b7db33;
        overflow: auto;
        align-content: flex-start;

        .default_item {
            width: 50%;
            padding: 5px;
            height: 110px;
            border: 1px solid #000;
            box-sizing: border-box;
            background: #ffffff;

            svg {
                width: 100px;
                height: 100px;
                * {
                    cursor: move;
                }
            }
        }
    }
}

/* g {
    cursor: move;
} */
</style >
<style scoped>
.cls-49 {
    text-anchor: end;
}

.cls-1,
.cls-18 {
    fill: #bebebe;
}

.cls-15,
.cls-17,
.cls-2,
.cls-3,
.cls-35,
.cls-36,
.cls-38,
.cls-4,
.cls-5,
.cls-7,
.cls-9 {
    fill: none;
}

.cls-2 {
    stroke: #e84646;
}

.cls-15,
.cls-17,
.cls-18,
.cls-19,
.cls-2,
.cls-21,
.cls-22,
.cls-23,
.cls-24,
.cls-25,
.cls-26,
.cls-27,
.cls-28,
.cls-29,
.cls-3,
.cls-33,
.cls-34,
.cls-35,
.cls-36,
.cls-38,
.cls-4,
.cls-40,
.cls-41,
.cls-42,
.cls-43,
.cls-44,
.cls-45,
.cls-46,
.cls-5,
.cls-7,
.cls-9 {
    stroke-miterlimit: 10;
}

.cls-17,
.cls-2,
.cls-3,
.cls-36,
.cls-4,
.cls-5,
.cls-7 {
    stroke-width: 3px;
}

.cls-3 {
    stroke: #0d42a0;
}

.cls-4 {
    stroke: #d9d900;
}

.cls-5 {
    stroke: #a52f00;
}

.cls-6 {
    fill: #a52f00;
}

.cls-7 {
    stroke: #e5e5e5;
}

.cls-8 {
    fill: #0d42a0;
}

.cls-9 {
    stroke: #d8d8d8;
}

.cls-15,
.cls-35,
.cls-9 {
    stroke-width: 4px;
}

.cls-10 {
    fill: #d8d8d8;
}

.cls-11,
.cls-20,
.cls-50 {
    font-size: 14px;
}

.cls-11,
.cls-20,
.cls-47,
.cls-51 {
    font-family: MicrosoftYaHeiLight, Microsoft YaHei;
}

.cls-12 {
    fill: #e84646;
}

.cls-13 {
    fill: #d9d900;
}

.cls-14 {
    fill: #e2e2e2;
}

.cls-15 {
    stroke: #7c7c7c;
}

.cls-16 {
    fill: #7c7c7c;
}

.cls-17 {
    stroke: #565656;
    stroke-dasharray: 5;
}

.cls-18 {
    stroke: #bebebe;
    stroke-width: 6px;
}

.cls-19,
.cls-21,
.cls-22,
.cls-23,
.cls-24,
.cls-25,
.cls-26,
.cls-27,
.cls-28,
.cls-29,
.cls-40,
.cls-41,
.cls-42,
.cls-43,
.cls-44,
.cls-45 {
    stroke: #1c1c1c;
}

.cls-19,
.cls-21,
.cls-22,
.cls-23,
.cls-24,
.cls-25,
.cls-26,
.cls-27,
.cls-28,
.cls-29,
.cls-40,
.cls-41,
.cls-42,
.cls-43,
.cls-44,
.cls-45,
.cls-46 {
    stroke-width: 0.5px;
}

.cls-19 {
    fill: url(#设备渐变灰色_2);
}

.cls-20 {
    letter-spacing: 0.02em;
}

.cls-21 {
    fill: url(#设备渐变灰色_2-2);
}

.cls-22 {
    fill: url(#设备渐变灰色_2-3);
}

.cls-23 {
    fill: url(#设备渐变灰色_2-4);
}

.cls-24 {
    fill: url(#设备渐变灰色_2-5);
}

.cls-25 {
    fill: url(#设备渐变灰色_2-6);
}

.cls-26 {
    fill: url(#设备渐变灰色_2-7);
}

.cls-27 {
    fill: url(#设备渐变灰色_2-8);
}

.cls-28 {
    fill: url(#设备渐变灰色_2-9);
}

.cls-29 {
    fill: url(#设备渐变灰色_2-10);
}

.cls-30 {
    fill: #eaeaea;
}

.cls-31 {
    fill: #404040;
}

.cls-32 {
    fill: #6c0;
}

.cls-33,
.cls-34,
.cls-49 {
    fill: lime;
}

.cls-33 {
    stroke: #40663c;
}

.cls-34,
.cls-35,
.cls-36,
.cls-38 {
    stroke: #51514f;
}

.cls-37 {
    fill: #51514f;
}

.cls-38 {
    stroke-width: 2px;
}

.cls-39 {
    fill: #919191;
    stroke: #333;
    stroke-linejoin: round;
    stroke-width: 0.75px;
}

.cls-40 {
    fill: url(#设备渐变灰色_2-11);
}

.cls-41 {
    fill: url(#设备渐变灰色_2-12);
}

.cls-42 {
    fill: url(#设备渐变灰色_2-13);
}

.cls-43 {
    fill: url(#设备渐变灰色_2-14);
}

.cls-44 {
    fill: url(#设备渐变灰色_2-15);
}

.cls-45 {
    fill: url(#设备渐变灰色_2-16);
}

.cls-46 {
    fill: #cecece;
    stroke: #6d6d6d;
}

.cls-47,
.cls-49 {
    font-size: 16px;
}

.cls-48 {
    fill: #020202;
}

.cls-49,
.cls-50 {
    font-family: MicrosoftYaHei, Microsoft YaHei;
}

.cls-51 {
    font-size: 20px;
}
</style>
