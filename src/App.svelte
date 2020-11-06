<script>
	import Header from "./UI/Header.svelte";
	import MeetupItem from "./Meetups/MeetupItem.svelte";

	const meetups = [
		{
			id: "m1",
			title: "Coding Bootcamp",
			subtitle: "Learn to code in 2 minutes",
			description:
				"In this meetup, we will have some experts that teach you how to code in 2 hours",
			imageUrl: "http://dummyImageUrl.pdf",
			address: "Hyderabad, India",
			contactEmail: "dummy@email.com",
		},
		{
			id: "m2",
			title: "Svelte",
			subtitle: "Learn Svelte in 2 minutes",
			description:
				"In this meetup, we will have some experts that teach you Svelte in 2 hours",
			imageUrl: "http://dummyImageUrl.pdf",
			address: "Hyderabad, India",
			contactEmail: "dummy@email.com",
		},
	];
</script>

<style>
	#meetups {
		margin-top: 5rem;
	}
</style>

<Header />

<section id ="meetups">
	{#each meetups as meetup, i (meetup.id)}
		<MeetupItem />
	{/each}
</section>
