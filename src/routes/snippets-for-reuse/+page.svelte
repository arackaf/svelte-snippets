<script lang="ts">
	import BasicSnippets from './BasicSnippets.svelte';

	type Review = {
		date: string;
		content: string;
	};
	type Product = {
		name: string;
		url: string;
		price: number;
		reviews?: Review[];
	};

	let searchedBook = $state<Product>({
		name: 'Effective TypeScript: 83 Specific Ways to Improve Your TypeScript, 2nd Edition',
		url: 'https://m.media-amazon.com/images/I/71eWL4AqPqL._SL1500_.jpg',
		price: 44.99,
		reviews: [
			{ date: '2/14/2024', content: 'Absolutely loved this book' },
			{ date: '6/2/2024', content: 'Even better than the first edition' }
		]
	});
	let relatedProduct = $state<Product>({
		name: 'Modern C++ Design: Generic Programming and Design Patterns Applied',
		url: 'https://m.media-amazon.com/images/I/914ncVx1hxL._SL1413_.jpg',
		price: 55.49
	});
</script>

<BasicSnippets />

{#snippet productReview(review: Review)}
	<div class="flex flex-row gap-3">
		<span>{review.date}</span>
		<span>{review.content}</span>
	</div>
{/snippet}

{#snippet productDisplay(p: Product)}
	<div class="flex flex-col gap-3">
		<div class="flex flex-row gap-3">
			<img class="max-w-[100px]" src={p.url} alt="product url" />
			<div class="flex flex-col">
				<h2 class="text-lg font-bold">{p.name}</h2>
				<span class="italic">${p.price.toFixed(2)}</span>
			</div>
		</div>
		<h3>Reviews:</h3>
		<div>
			{#each p.reviews ?? [] as review}
				{@render productReview(review)}
			{/each}
		</div>
	</div>
{/snippet}

<section class="flex flex-col gap-5">
	<h1 class="mb-5 text-3xl">Product Display Page</h1>

	{@render productDisplay(searchedBook)}

	<aside>You might also be interested in:</aside>

	{@render productDisplay(relatedProduct)}
</section>
