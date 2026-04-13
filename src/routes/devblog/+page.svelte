<script lang="ts">
	import { Carousel } from '@skeletonlabs/skeleton-svelte';
  import { resolve } from '$app/paths';

	const { data } = $props();

</script>


<main>
<Carousel slideCount={data.posts.length} slidesPerPage={2} spacing="16px" loop>
	<Carousel.Control class="flex justify-between mb-4">
		<Carousel.PrevTrigger class="btn preset-filled">
			<span>&larr;</span>
			<span>Back</span>
		</Carousel.PrevTrigger>
		<Carousel.NextTrigger class="btn preset-filled">
			<span>Next</span>
			<span>&rarr;</span>
		</Carousel.NextTrigger>
	</Carousel.Control>
	<Carousel.ItemGroup>
		{#each data.posts as slide ,i}
    <a href={resolve("/devblog/"+slide.name)}>
			<Carousel.Item index={i} class="card bg-surface-100-900 h-50 p-4 flex justify-center items-center">
				{slide.title}
			</Carousel.Item>
      </a>
		{/each}
	</Carousel.ItemGroup>
	<Carousel.IndicatorGroup>
		<Carousel.Context>
			{#snippet children(carousel)}
				{#each carousel().pageSnapPoints as _, index}
					<Carousel.Indicator {index} />
				{/each}
			{/snippet}
		</Carousel.Context>
	</Carousel.IndicatorGroup>
</Carousel>

</main>


<style>

  main{
    width: 100vw;
    height: 60vh;
    padding: 5vh;
    display: flex;
    justify-content: center;
    align-items: center;    
  }
</style>