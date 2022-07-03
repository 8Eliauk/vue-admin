<template>
  <div>
    <el-card class="box-card" style="margin: 10px 0px">
      <div slot="header" class="clearfix">
        <!-- 头部左侧内容 -->
        <el-tabs class="tab" v-model="activeName">
          <el-tab-pane label="销售额" name="sale"></el-tab-pane>
          <el-tab-pane label="访问量" name="visite"></el-tab-pane>
        </el-tabs>
        <!-- 头部右侧内容 -->
        <div class="right">
          <span @click="setDay">今日</span>
          <span @click="setWeek">本周</span>
          <span @click="setMonth">本月</span>
          <span @click="setYear">本年</span>
          <el-date-picker
            v-model="date"
            class="date"
            type="daterange"
            range-separator="-"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            size="mini"
            value-format="yyyy-MM-dd"
          >
          </el-date-picker>
        </div>
      </div>
      <div>
        <el-row :gutter="10">
          <el-col :span="18">
            <!-- 容器 -->
            <div class="charts" ref="charts"></div>
          </el-col>
          <el-col :span="6">
            <h3>门店{{ title }}排名</h3>
            <ul>
              <li>
                <span class="rindex">1</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">2</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">3</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">4</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">5</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">6</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">7</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
              <li>
                <span class="rindex">8</span>
                <span>肯德基</span>
                <span>123455</span>
              </li>
            </ul>
          </el-col>
        </el-row>
      </div>
    </el-card>
  </div>
</template>

<script>
// 引入echarts
import * as echarts from "echarts";
import dayjs from "dayjs";
import { mapState } from "vuex";
export default {
  name: "Sale",
  data() {
    return {
      activeName: "sale",
      mycharts: null,
      // 收集日历的数据
      date: [],
    };
  },
  mounted() {
    //  初始化echarts实例
    this.mycharts = echarts.init(this.$refs.charts);
    // 配置数据
    this.mycharts.setOption({
      title: {
        text: "销售额趋势",
      },
      tooltip: {
        trigger: "axis",
        axisPointer: {
          type: "shadow",
        },
      },
      grid: {
        left: "3%",
        right: "4%",
        bottom: "3%",
        containLabel: true,
      },
      xAxis: [
        {
          type: "category",
          data: [],
          axisTick: {
            alignWithLabel: true,
          },
        },
      ],
      yAxis: [
        {
          type: "value",
        },
      ],
      series: [
        {
          name: "Direct",
          type: "bar",
          barWidth: "60%",
          data: [],
        },
      ],
    });
    // 顶部是mounted: 为什么第一次没有数据，没有数据因此不显示
  },
  computed: {
    // 计算属性-标题
    title() {
      return this.activeName == "sale" ? "销售额" : "访问量";
    },
    //
    ...mapState({
      listState: (state) => state.home.list,
    }),
  },
  // 监听属性
  watch: {
    title() {
      //   重新修改图标的配置数据
      this.mycharts.setOption({
        title: {
          text: this.title + "趋势",
        },
        xAxis: {
          data:
            this.title == "销售额"
              ? this.listState.orderFullYearAxis
              : this.listState.userFullYearAxis,
        },
        series: [
          {
            data:
              this.title == "销售额"
                ? this.listState.orderFullYear
                : this.listState.userFullYear,
          },
        ],
      });
    },
    listState() {
      this.mycharts.setOption({
        title: {
          text: "销售额趋势",
        },
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "shadow",
          },
        },
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          containLabel: true,
        },
        xAxis: [
          {
            type: "category",
            data: this.listState.orderFullYearAxis,
            axisTick: {
              alignWithLabel: true,
            },
          },
        ],
        yAxis: [
          {
            type: "value",
          },
        ],
        series: [
          {
            name: "Direct",
            type: "bar",
            barWidth: "60%",
            data: this.listState.orderFullYear,
            color:'yellowgreen'
          },
        ],
      });
    },
  },
  methods: {
    // 本天
    setDay() {
      const day = dayjs().format("YYYY-MM-DD");
      this.date = [day, day];
    },
    // 本周
    setWeek() {
      const start = dayjs().day(1).format("YYYY-MM-DD");
      const end = dayjs().day(7).format("YYYY-MM-DD");
      this.date = [start, end];
    },
    // 本月
    setMonth() {
      const start = dayjs().startOf("month").format("YYYY-MM-DD");
      const end = dayjs().endOf("month").format("YYYY-MM-DD");
      this.date = [start, end];
    },
    // 本年
    setYear() {
      const start = dayjs().startOf("year").format("YYYY-MM-DD");
      const end = dayjs().endOf("year").format("YYYY-MM-DD");
      this.date = [start, end];
    },
  },
};
</script>

<style scoped>
.clearfix {
  display: flex;
  justify-content: space-between;
  position: relative;
}
.tab {
  width: 100%;
}
.right {
  right: 0;
  position: absolute;
}
.right span {
  margin: 0px 10px;
}
.date {
  width: 240px;
  margin: 0px 20px;
}
.charts {
  width: 100%;
  height: 300px;
  border: 1px solid red;
}
ul {
  list-style: none;
  width: 100%;
  height: 300px;
  padding: 0;
}
ul li {
  height: 8%;
  margin: 5px 0;
}
ul li span {
  margin: 0px 6px;
}
ul li span:last-child {
  float: right;
}
ul li:nth-child(-n + 3) .rindex {
  width: 20px;
  height: 20px;
  display: inline-block;
  border-radius: 50%;
  background: black;
  color: white;
  text-align: center;
  line-height: 20px;
}
.rindex {
  width: 20px;
  height: 20px;
  display: inline-block;
  color: black;
  text-align: center;
  line-height: 20px;
}
</style>