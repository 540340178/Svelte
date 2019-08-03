<div>
    {#if data}
        {#each data as item}
            <div class="car_every">
                <img src={item.src} alt=""/>
                <div class="right">
                    <div>{item.name}</div>
                    <div>￥：{item.price}元</div>
                    <div><span on:click={() => {
                        jian(item.id)
                    }}>-</span><span class="num">{item.num}</span><span on:click={() => {
                        jia(item.id)
                    }}>+</span></div>
                </div>
            </div>
        {/each}
    {/if}
    <div class="zong"><div>共 {num || 0} 件</div> <div>总计：￥{sum || 0}元</div></div>
</div>



<script>
let data = JSON.parse(localStorage.getItem('car'));
let num=0;
let sum = 0;
function sum_price() {
    sum = data && data.reduce((prev,item)=>{
        return prev+item.num * item.price
    },0);
    num = data && data.reduce((prev,item)=>{
        return prev+item.num
    },0)
}
sum_price();
function jian(id) {
    let ind = data.findIndex((item) => {
        return item.id === id
    });
    data[ind].num--;
    if(data[ind].num<=0){
        data.splice(ind,1);
    };
    sum_price();
    localStorage.setItem('car',JSON.stringify(data))
}
function jia(id) {
    let ind = data.findIndex((item) => {
        return item.id === id
    });
    data[ind].num++;
    sum_price();
    localStorage.setItem('car',JSON.stringify(data))
}
</script>

<style>
.car_every{
    height: 150px;
    width: 100%;
    border: 1px solid #ccc;
    box-sizing: border-box;
    margin: 5px 0;
    display: flex;
    align-items: center;
    padding: 0 10px;
}
img{
    width: 130px;
    height: 130px;
    border: 1px solid #eee;
}
.right{
    padding: 10px 0;
    flex: 1;
    margin-left: 10px;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
}
.right>div{
    display: flex;
}
span{
    width: 30px;
    height: 30px;
    border: 1px solid #ccc;
    display: inline-block;
    font-size: 25px;
    text-align: center;
    line-height: 30px;
}
.num{
    font-size: 15px;
}
.zong{
    display: flex;
    justify-content: space-between;
}
</style>