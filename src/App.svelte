<script>
	export let name;
	export let country = "India";

	$: uppercaseName = name.toUpperCase();

	const changeNameHandler = () => {
		name ="Badhon Kundu";
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello I am {uppercaseName}, and I am from {country}!</h1>
<button on:click="{changeNameHandler}"> Get full name</button>
<input bind:value="{name}" />
