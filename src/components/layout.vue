<template>
    <div>
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <defs>
                <linearGradient id="设备渐变灰色_2" x1="1146.5" y1="-266" x2="1146.5" y2="-353.5"
                    gradientTransform="translate(747 1670) rotate(-90)" gradientUnits="userSpaceOnUse">
                    <stop offset="0" stop-color="#818181" />
                    <stop offset="0.51" stop-color="#bdbdbd" />
                    <stop offset="1" stop-color="#818181" />
                </linearGradient>
                <linearGradient id="设备渐变灰色_2-2" x1="1146.5" y1="-67" x2="1146.5" y2="-154.5" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-3" x1="1248.8" y1="342.5" x2="1303" y2="342.5"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-4" x1="1248.8" y1="386.7" x2="1303" y2="386.7"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-5" x1="1114.81" y1="1078.09" x2="1169.01" y2="1078.09"
                    gradientTransform="translate(2417.81 1377.39) rotate(180)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-6" x1="1395.8" y1="207" x2="1459" y2="207"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-7" x1="1376.8" y1="486.5" x2="1475" y2="486.5"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-8" x1="1376.8" y1="698.75" x2="1475" y2="698.75"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-9" x1="958.81" y1="1211.14" x2="1022.01" y2="1211.14"
                    gradientTransform="translate(2417.81 1377.39) rotate(180)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-10" x1="1376.5" y1="267.5" x2="1474.5" y2="267.5"
                    gradientTransform="matrix(1, 0, 0, 1, 0, 0)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-11" x1="662" y1="493" x2="671" y2="493"
                    gradientTransform="translate(-238 -364)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-12" x1="659" y1="482.2" x2="674" y2="482.2"
                    gradientTransform="translate(-227.2 -353.2)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-13" x1="659" y1="503.8" x2="674" y2="503.8"
                    gradientTransform="translate(-248.8 -374.8)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-14" x1="640" y1="418" x2="649" y2="418"
                    gradientTransform="translate(-141 -311)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-15" x1="637" y1="407.2" x2="652" y2="407.2"
                    gradientTransform="translate(-130.2 -300.2)" xlink:href="#设备渐变灰色_2" />
                <linearGradient id="设备渐变灰色_2-16" x1="637" y1="428.8" x2="652" y2="428.8"
                    gradientTransform="translate(-151.8 -321.8)" xlink:href="#设备渐变灰色_2" />
            </defs>
            <!-- <path class="cls-19"
                d="M 403.6 571.17 l -10.1 -11 v -77 L 403.6 474 h 63.94 L 481 481.33 V 562 l -16.83 11 S 401.91 571.17 403.6 571.17 Z" /> -->
            <text class="cls-20" transform="translate(431 530.84)">E5</text>
            <circle class="test" draggable="true" @click="handleMove" cx="50" cy="50" r="40" stroke="black" stroke-width="2"
                fill="red" />
            <g id="大型设备">

                <!-- 
                <path class="cls-21"
                    d="M602.6,571.17l-10.1-11v-77L602.6,474h63.94L680,481.33V562l-16.83,11S600.91,571.17,602.6,571.17Z" />
                <text class="cls-20" transform="translate(630 530.84)">E4</text> -->
                <!-- <polygon class="cls-22"
                    points="1303 307 1248.8 307 1248.8 316.34 1248.8 362.81 1248.8 378 1303 378 1303 307" />
                <path class="cls-23" d="M1248.8,378.5c0,9.05,12.14,16.39,27.1,16.39s27.1-7.34,27.1-16.39Z" />
                <path class="cls-24" d="M1303,307.5c0-9.05-12.13-16.39-27.09-16.39s-27.1,7.34-27.1,16.39Z" />
                <polygon class="cls-25"
                    points="1459 176 1395.8 176 1395.8 184.16 1395.8 224.73 1395.8 238 1459 238 1459 176" />
                <polygon class="cls-26"
                    points="1475 298 1376.8 298 1376.8 347.59 1376.8 594.32 1376.8 675 1475 675 1475 298" />
                <path class="cls-27" d="M1376.8,675.5c0,25.68,22,46.5,49.1,46.5s49.1-20.82,49.1-46.5Z" />
                <path class="cls-28" d="M1459,176.5c0-11.32-14.15-20.5-31.6-20.5s-31.6,9.18-31.6,20.5Z" />
                <path class="cls-29" d="M1395.5,237.5l-19,60h98l-16-60Z" />
                <text class="cls-20" transform="translate(1420 173.84)">C2</text>
                <text class="cls-20" transform="translate(1420 636.84)">C1</text>
                <text class="cls-20" transform="translate(1420 479.84)">K1</text> -->
            </g>
        </svg>
    </div>
</template>
<script>


export default {
    name: "layout",
    data() {
        return {

        };
    },
    methods: {
        handleMove() {
            console.log("move");
        }
    },
    mounted() {

    }
};
</script>
<style  scoped>
svg {
    width: 100%;
    height: 100vh;
}

.test {
    cursor: move;
}
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
