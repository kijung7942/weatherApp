<template>
  <div>
	<ul class="city-selector">
		<li 
			@click="selectCity(city)"
			:class="{isSelected: city.selected}" 
			v-for="city in cities" 
			:key="city.code">
			{{city.label}}
		</li>
	</ul>
  </div>
</template>

<script>
export default {
	name: 'CitySelector',
	data(){
		return {
			cities: [
				{ code: "Seoul", lat: "37.5666791", lon: "126.9782914", label: "서울", selected: false },
				{ code: "Tokyo", lat: "35.6828387", lon: "139.7594549", label: "도쿄", selected: false },
				{ code: "London", lat: "51.5073219", lon: "-0.1276474", label: "런던", selected: false },
				{ code: "Moscow", lat: "55.7504461", lon: "37.6174943", label: "모스크바", selected: false },
				{ code: "Yakutsk", lat: "62.0274078", lon: "129.7319787", label: "야크추크", selected: false },
			]
		}
	},
	methods: {
		selectCity(city) {
			city.selected = !city.selected;
			this.$emit("selectCity", city);
		}
	}
}
</script>

<style scoped>
	.city-selector {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
	}
	.city-selector li {
		display: flex;
		justify-content: center;
		align-items: center;
		border: 0.1em solid #efefef;
		padding: 0.3em;
		cursor: pointer;
	}
	.isSelected {
		background: #fd1d1d;
		color: #efefef;
	}
</style>