<div class="wrap">
	<Router>
		<h3><Link to='/'><img class="icon" src="/menu.png" alt=""/></Link>京东超市<Link to='/shop_car'><img class="icon" src="/car.png" alt=""/></Link></h3>
		<div class="view">
				<Route path="/" component={ShopLidt}></Route>
				<Route path="/shop_car" component={ShopCar}></Route>
		</div>
	</Router>
</div>



<script>
import ShopLidt from './shopList.svelte'
import ShopCar from './shopCar.svelte'
import {Router,Route,Link} from 'svelte-routing'
</script>

<style>
*{
	margin: 0;
	padding: 0;
}
html,body{
	width: 100%;
	height: 100%;
	overflow: hidden;
}
h3{
	text-align: center;
	background: #f00;
	color: #fff;
	height: 50px;
	line-height: 50px;
	display: flex;
	justify-content: space-between;
	align-items: center;
	padding: 0 15px;
}
.wrap{
	height: 100%;
	width: 100%;
	display: flex;
	flex-direction: column;
}
.view{
	flex: 1;
}
.icon{
	width: 25px;
	height: 25px;
}
a{
	height: 25px;
}
</style>