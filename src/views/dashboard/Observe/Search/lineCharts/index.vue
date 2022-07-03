<template>
    <div>
        <div class="header">
            <span class="search-header">搜索用户数</span>
            <svg t="1652974455753" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2970" width="26" height="26"><path d="M512 179.2a332.8 332.8 0 1 1 0 665.6 332.8 332.8 0 0 1 0-665.6z m0 51.2a281.6 281.6 0 1 0 0 563.2 281.6 281.6 0 0 0 0-563.2z" p-id="2971" fill="#707070"></path><path d="M512.768 339.968a38.7072 38.7072 0 1 1 0 77.3632 38.7072 38.7072 0 0 1 0-77.3632zM546.4576 678.6048h-27.2384c-14.2848 0-29.0304-12.3904-29.0304-23.7056V498.0224h-9.728a25.8048 25.8048 0 1 1 0-51.6096s31.488-0.1024 32.3072 0c13.1072 0.9728 22.5792 6.656 22.5792 17.3568v163.2768h11.1104a25.8048 25.8048 0 1 1 0 51.5584z" p-id="2972" fill="#707070"></path></svg>
        </div>
        <div class="main">
            <span class="main-title">12321</span>
            <span class="main-content">17.1</span>
            <svg t="1652976086160" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1903" width="10" height="10"><path d="M573.056 272l308.8 404.608A76.8 76.8 0 0 1 820.736 800H203.232a76.8 76.8 0 0 1-61.056-123.392L450.976 272a76.8 76.8 0 0 1 122.08 0z" fill="#d81e06" p-id="1904"></path></svg>
            <svg t="1652976191141" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="7555" width="10" height="10"><path d="M573.056 752l308.8-404.608A76.8 76.8 0 0 0 820.736 224H203.232a76.8 76.8 0 0 0-61.056 123.392l308.8 404.608a76.8 76.8 0 0 0 122.08 0z" fill="#00c97c" p-id="7556"></path></svg>
        </div>
        <div class="footer">
            <div class="charts" ref="charts"></div>
        </div>
    </div>
</template>

<script>
    // 引入echarts
    import * as echarts from 'echarts';
    export default {
        name:'lineCharts',
        mounted() {
            // 初始化echarts实例
            let lineCharts = echarts.init(this.$refs.charts);
            // 配置数据
            lineCharts.setOption({
                xAxis: {
                    // 隐藏x轴
                    show:false,
                    type: 'category'
                },
                yAxis: {
                    // 隐藏y轴
                    show:false,
                },
                // 系列
                series:[
                    {
                        type:'line',
                        data:[30,7,33,12,48,9,29,10,44],
                        // 拐点的样式的设置
                        itemStyle: {
                            opacity:0
                        },
                        // 线条以平滑的形式出现
                        smooth: true,
                        // 填充风格
                        areaStyle: {
                            color: {
                                type:'linear',
                                x:0,
                                y:0,
                                x2:0,
                                y2:1,
                                colorStops: [
                                    {
                                        offset:0,
                                        color: "blue", // 0% 处是purple颜色
                                    },
                                    {
                                        offset:1,
                                        color: "#fff", // 100% 处的颜色
                                    },
                                ],
                                global: false, // 缺省为 false
                            }   
                        }
                    }
                ],
                // 布局调试
                grid: {
                    left:0,
                    top:0,
                    right:0,
                    bottom:0
                }
            })
        }
    }
</script>

<style scoped>
.header {
    display: flex;
    align-items: center;
}
.search-header {
    margin-right: 20px;
}
.main {
    margin: 10px 0px;
}
.main-title {
    margin-right: 30px;
}
.main-content {
    margin-right: 8px;
}
.charts {
    width: 100%;
    height: 50px;
}
</style>