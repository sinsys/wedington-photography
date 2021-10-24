<script lang="ts">
	import Viewport from './components/Viewport.svelte';
</script>

<main>
	<Viewport />
</main>

<style type="scss">
	@import './styles/base';
	main {
		@include page;
		background: $baseBlue;
		color: $light;
	}
</style>