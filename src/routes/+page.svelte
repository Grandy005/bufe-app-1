<script>
	import {onMount} from 'svelte';
	import {writable} from 'svelte/store'

	import {fade} from 'svelte/transition';
	let etel = "/images/hambi.jpeg";
	let pizza = "/images/pizza.jpg";
	let melegszendvics = "/images/sajtos-sonkas-melegszendvics.jpg";
	let hotdog = "/images/hotdog.jpeg";
	let pogi = "/images/pogi.jpeg";
	let ital = "/images/cola.jpeg";
	let nasi = "/images/chips.jpeg";
	let egyeb = "/images/zsepi.jpeg";
	let cardRow;

	const cardStore = writable(null);

	onMount(() => {
		let cards = cardRow.querySelectorAll(".navCard");
		cardStore.set(cards);

		cards.forEach(card => {
			card.addEventListener("click", HandleClick)
			card.classList.add("opacity-100");
		})
	})

	function HandleClick(e) {
		OpacitySet();
		let eventTarget = e.target.closest(".navCard");
		eventTarget.classList.remove("opacity-60");
		eventTarget.classList.add("opacity-100");
	}

	function OpacitySet() {
		$cardStore.forEach(card => {
			card.classList.remove("opacity-100");
			card.classList.add("opacity-60");
		})
	}
	
</script>

<main in:fade={{duration: 180}} class="flex flex-col h-screen items-center">

	<div class="topBar">
		<div class="topRow">
			<h1 class="text-red-1 drop-shadow-md font-extrabold text-4xl text-left pl-4">Kandó Büfé</h1>
			<img src="/images/avatar/2289_SkVNQSBGQU1PIDEwMjgtMTIy.svg" alt="" class="w-24 h-24 pr-4">
		</div>
		<div bind:this={cardRow} class="cardRow">
			<div class="navCard">
				<img src={etel} alt="hamburger" class="img">
				<p class="text-center bg-white text-red-1 p-2 text-lg font-semibold rounded-b-md">Ételek</p>
			</div>
			<div class="navCard">
				<img src={ital} alt="cola" class="img">
				<p class="text-center bg-white text-red-1 p-2 text-lg font-semibold rounded-b-md">Italok</p>
			</div>
			<div class="navCard">
					<img src={nasi} alt="macska burger" class="img">
					<p class="text-center bg-white text-red-1 p-2 text-lg font-semibold rounded-b-md">Nasik</p>
			</div>
			<div class="navCard">
					<img src={egyeb} alt="macska burger" class="img">
					<p class="text-center bg-white text-red-1 p-2 text-lg font-semibold rounded-b-md">Egyéb</p>
			</div>
		</div>
	</div>

	<div class="foodCol">
		<div class="foodCard">
			<div class="basis-1/3">
				<img src={etel} alt="" class="w-28 h-28 rounded-md">
			</div>
			<div class="flex flex-col items-center justify-between basis-2/3">
				<div>
					<h3 class="mt-2 font-semibold text-red-1 text-lg text-center">Fullos hamburger</h3>
					<p class="text-center text-sm py-1 px-2">100%-ban kézzel készült friss és finom burger.</p>
				</div>
				<div class="flex flex-row justify-end items-center w-40 ml-10">
					<p class="font-semibold">800 Ft</p>
				</div>
			</div>
		</div>
		<div class="foodCard">
			<div class="basis-1/3">
				<img src={pizza} alt="" class="w-28 h-28 rounded-md">
			</div>
			<div class="flex flex-col items-center justify-between basis-2/3">
				<div>
					<h3 class="mt-2 text-red-1 font-semibold text-lg text-center">Kandós pizza</h3>
					<p class= "text-center text-sm py-1 px-2">A világ legfinomabb sonkás-sajtos pizzája. Ennyi.</p>
				</div>
				<div class="flex flex-row justify-end w-40 ml-10">
					<p class="font-semibold">600 Ft</p>
				</div>
			</div>
		</div>
		<div class="foodCard">
			<div class="basis-1/3">
				<img src={melegszendvics} alt="" class="w-28 h-28 rounded-md">
			</div>
			<div class="flex flex-col items-center justify-between basis-2/3">
				<div>
					<h3 class="mt-2 text-red-1 font-semibold text-lg text-center">Francia pirítós</h3>
					<p class=" text-center text-sm py-1 px-2">Egy melegszendvics ami után garantáltan nem maradsz éhes.</p>
				</div>
				<div class="flex flex-row justify-end w-40 ml-10">
					<p class="font-semibold">550 Ft</p>
				</div>
			</div>
		</div>
		<div class="foodCard">
			<div class="basis-1/3">
				<img src={hotdog} alt="" class="w-28 h-28 rounded-md">
			</div>
			<div class="flex flex-col items-center justify-between basis-2/3">
				<div>
					<h3 class="mt-2 text-red-1 font-semibold text-lg text-center">Hot dog</h3>
					<p class="text-center text-sm py-1 px-2">Kérheted ketchuppal, majonézzel, mustárral is.</p>
				</div>
				<div class="flex flex-row justify-end w-40 ml-10">
					<p class="font-semibold">500 Ft</p>
				</div>
			</div>
		</div>
		<div class="foodCard">
			<div class="basis-1/3">
				<img src={pogi} alt="" class="w-28 h-28 rounded-md">
			</div>
			<div class="flex flex-col items-center justify-between basis-2/3">
				<div>
					<h3 class="mt-2 text-red-1 font-semibold text-lg text-center">Pogácsa</h3>
					<p class="text-center text-sm py-1 px-2">Az ikonikus kandós pogi amit mindenki szeret.</p>
				</div>
				<div class="flex flex-row justify-end w-40 ml-10">
					<p class="font-semibold">300 Ft</p>
				</div>
			</div>
		</div>
	</div>
</main>