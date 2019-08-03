<div class="list">
    {#each data as item}
        <div class="list_every">
            <img src={item.src} alt=""/>
            <div>{item.name}</div>
            <div>￥：{item.price} 元</div>
            <button on:click={() => {
                //window.localStorage.setItem('name',item.id)
                let car = JSON.parse(window.localStorage.getItem('car') || '[]');
                let ind = car.findIndex(ele => {
                    return ele.id === item.id
                })
                if(ind === -1){
                    item.num++;
                    car.push(item)
                }else{
                    car[ind].num+=1;
                }
                window.localStorage.setItem('car',JSON.stringify(car));
            }}>加入购物车</button>
        </div>
    {/each}
    
</div>

<script>
import { onMount } from 'svelte';
import axios from 'axios'
let data = [];
onMount(function() {
    axios.get('http://169.254.213.212:7001/').then((res) => {
            data = res.data;
	})
})
</script>

<style>
.list_every{
    width: 48.5%;
    border: 1px solid #ccc;
    box-sizing: border-box;
    margin: 2.5px;
    justify-content: space-between;
    align-items: center;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 10px 0;
}
.list{
    display: flex;
    flex-wrap: wrap;
}
img{
    width:100%;
    height: 200px;
}
</style>

