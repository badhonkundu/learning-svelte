<script>
	import ContactCard from "./ContactCard.svelte";
	export let name;
	export let country = "India";

	let jobTitle = "";
	let description = "";
	let imgUrl = "";

	$: uppercaseName = name.toUpperCase();

	const changeNameHandler = () => {
		name = "Badhon Kundu";
	};
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello I am {uppercaseName}, and I am from {country}!</h1>
<button on:click={changeNameHandler}> Get full name</button>
<input bind:value={name} />
<input bind:value={jobTitle} />
<input bind:value={imgUrl} />
<textarea bind:value={description} />

<!--
sending props to contactcard componnet
{description} and {jobTitle} are examples of self extending prop 
-->
<ContactCard userName={name} {jobTitle} {description} {imgUrl} />
