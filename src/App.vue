<template>
	<div class="app">
		<header>
			<div class="title">
				<img src="./assets/heart.svg" alt="site logo" />
				<h1>Hyrule Jobs</h1>
			</div>
			<div class="order">
				<button @click="handleClick('title')">order by title</button>
				<button @click="handleClick('salary')">order by salary</button>
				<button @click="handleClick('location')">order by location</button>
			</div>
		</header>
		<JobList :jobs="jobs" :order="order" />
	</div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "@/components/JobList.vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
	name: "App",
	components: { JobList },
	setup() {
		// Data:
		const jobs = ref<Job[]>([
			{ id: "1", title: "Farm Worker", location: "Lon Lon Ranch", salary: 30000, description: "Responsible for daily farm tasks including feeding animals and harvesting crops." },
			{ id: "2", title: "Quarryman", location: "Death Mountain", salary: 40000, description: "Extracts valuable minerals and stones from the quarry." },
			{ id: "3", title: "Flute Player", location: "The Lost Woods", salary: 35000, description: "Plays the flute to entertain and guide travelers through the woods." },
			{ id: "4", title: "Cucco Keeper", location: "Kakariko Village", salary: 32000, description: "Takes care of the cuccos, ensuring they are fed and healthy." },
			{ id: "5", title: "Mask Salesman", location: "Clock Town", salary: 38000, description: "Sells a variety of magical and non-magical masks to customers." },
			{ id: "7", title: "Fisherman", location: "Lake Hylia", salary: 34000, description: "Catches fish and maintains fishing equipment." },
			{ id: "8", title: "Prison Guard", location: "Gerudo Valley", salary: 32000, description: "Guards the prison and ensures the security of inmates." },
			{ id: "9", title: "Chef", location: "Zora's Domain", salary: 36000, description: "Prepares meals for the residents and visitors of Zora's Domain." },
			{ id: "10", title: "Blacksmith", location: "Goron City", salary: 39000, description: "Forges and repairs weapons and tools." },
			{ id: "11", title: "Postman", location: "Hyrule Castle Town", salary: 33000, description: "Delivers letters and packages throughout Hyrule Castle Town." },
			{ id: "12", title: "Swordsmith", location: "Kokiri Forest", salary: 37000, description: "Crafts and sharpens swords for warriors and adventurers." },
			{ id: "13", title: "Carpenter", location: "Hateno Village", salary: 35000, description: "Builds and repairs structures and furniture." },
			{ id: "14", title: "Priest", location: "Temple of Time", salary: 38000, description: "Conducts religious ceremonies and maintains the temple." }
		]);

		const order = ref<OrderTerm>("title");

		// Methods:
		const handleClick = (newTerm: OrderTerm) => {
			order.value = newTerm;
		};

		return { jobs, order, handleClick };
	}
});
</script>

<style>
header {
	text-align: center;
}
header .order {
	margin-top: 20px;
}
button {
	margin: 0 10px;
	color: #1195c9;
	border: 3px solid #1195c9;
	background: #d5f0ff;
	padding: 8px 16px;
	border-radius: 4px;
	cursor: pointer;
	font-weight: bold;
}
header .title {
	display: flex;
	justify-content: center;
}
header img {
	width: 60px;
	margin-right: 20px;
}
header h1 {
	font-size: 3em;
}
</style>
