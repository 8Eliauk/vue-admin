<template>
    <div>
        <el-row :gutter="10">
            <el-col :span="6">
                <el-card>
                    <!-- 第一个card -->
                    <Detail title="总销售额" count="￥126560">
                        <template slot="charts">
                            <span>周同比 56.67% <svg t="1652976086160" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1903" width="8" height="8"><path d="M573.056 272l308.8 404.608A76.8 76.8 0 0 1 820.736 800H203.232a76.8 76.8 0 0 1-61.056-123.392L450.976 272a76.8 76.8 0 0 1 122.08 0z" fill="#d81e06" p-id="1904"></path></svg></span>
                            &nbsp;<span>日同比 19.16% <svg t="1652976191141" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="7555" width="8" height="8"><path d="M573.056 752l308.8-404.608A76.8 76.8 0 0 0 820.736 224H203.232a76.8 76.8 0 0 0-61.056 123.392l308.8 404.608a76.8 76.8 0 0 0 122.08 0z" fill="#00c97c" p-id="7556"></path></svg></span>
                        </template>
                        <template slot="footer">
                            <span>日销售额￥12423</span>
                        </template>
                    </Detail>
                </el-card>
            </el-col>
            <el-col :span="6">
                <el-card>
                    <!-- 第二个card -->
                    <Detail title="访问量" count="88460">
                        <template slot="charts">
                            <lineCharts></lineCharts>
                        </template>
                        <template slot="footer">
                            <span>日访问量1234</span>
                        </template>
                    </Detail>
                </el-card>
            </el-col>
            <el-col :span="6">
                <el-card>
                    <!-- 第三个card -->
                    <Detail title="支付笔数" count="88460">
                        <template slot="charts">
                            <barCharts></barCharts>
                        </template>
                        <template slot="footer">
                            <span>转化率 65%</span>
                        </template>
                    </Detail>
                </el-card>
            </el-col>
            <el-col :span="6">
                <el-card>
                    <!-- 第四个card -->
                    <Detail title="运营活动效果" count="78%">
                        <template slot="charts">
                            <progressCharts></progressCharts>
                        </template>
                        <template slot="footer">
                            <span>周同比 12% <svg t="1652976086160" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="1903" width="8" height="8"><path d="M573.056 272l308.8 404.608A76.8 76.8 0 0 1 820.736 800H203.232a76.8 76.8 0 0 1-61.056-123.392L450.976 272a76.8 76.8 0 0 1 122.08 0z" fill="#d81e06" p-id="1904"></path></svg></span>
                            &nbsp;<span>日同比 11% <svg t="1652976191141" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="7555" width="8" height="8"><path d="M573.056 752l308.8-404.608A76.8 76.8 0 0 0 820.736 224H203.232a76.8 76.8 0 0 0-61.056 123.392l308.8 404.608a76.8 76.8 0 0 0 122.08 0z" fill="#00c97c" p-id="7556"></path></svg></span>
                        </template>
                    </Detail>
                </el-card>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    import Detail from './Detail';
    import lineCharts from './lineChart';
    import barCharts from './barCharts';
    import progressCharts from './progressCharts'
    export default {
        name:'Card',
        components: {
            Detail,
            lineCharts,
            barCharts,
            progressCharts
        }
    }
</script>

<style scoped>

</style>