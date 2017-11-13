<template>
	 <div class="touch">
      <scroll :on-refresh="onRefresh" :on-infinite="onInfinite" :dataList="scrollData">
          <ul class="list">
              <li v-for="(item,index) in listdata">{{item.date}}</li>
							<li v-for="(item,index) in downdata">{{item.date}}</li>
          </ul>
      </scroll>
    </div>
</template>
<script>
import scroll from './Refresh'
	export default{
		data(){
			return{
				counter: 1, //当前页
				num: 10, // 一页显示多少条
				pageStart: 0, // 开始页数
				pageEnd: 0, // 结束页数
				listdata: [], // 下拉更新数据存放数组
				downdata: [], // 上拉更多的数据存放数组
				scrollData:{
					noFlag: false //暂无更多数据显示
				}
			}
		},
		components:{
			scroll
		},
		mounted: function() {
      this.getList();
    },
    methods:{
    	getList() {
          var response = []
          for(let i = 0; i < 20; i++) {
              response.push({
                  date: "number"+i
              })
          }
          this.listdata = response.slice(0, this.num);
      },
      onRefresh(done) {
           this.getList();
           done(); // call done
      },
      onInfinite(done) {
				this.counter++;
				let end = this.pageEnd = this.num * this.counter;
				let i = this.pageStart = this.pageEnd - this.num;

				let more = this.$el.querySelector('.load-more')
				for(i; i < end; i++) {
					if(i >= 30) {
						more.style.display = 'none'; //隐藏加载条

						//走完数据调用方法
						this.scrollData.noFlag = true;

						break;
					} else {
						this.downdata.push({
							name: i + "==="
						})
						more.style.display = 'none'; //隐藏加载条
					}
				}

				done();
			}
    }
	}
</script>
<style>
	.touch .list li {
		text-align: left!important;
		font-size: 18px;
		padding: 15px 10px;
		text-align: center;
		border-bottom: 1px solid #E6E6E6;
	}
</style>