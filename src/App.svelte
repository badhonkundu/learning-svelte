<script>
	import Header from "./UI/Header.svelte";
	import MeetupGrid from "./Meetups/MeetupGrid.svelte";
	import EditMeetup from "./Meetups/EditMeetup.svelte";
	import TextInput from "./UI/TextInput.svelte";
	import Button from "./UI/Button.svelte";

	let constImageUrl =
		"https://upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Speyer_-_Altp%C3%B6rtel_-_Blick_auf_Domfassade_und_Kircht%C3%BCrme_mit_Abendsonne.jpg/750px-Speyer_-_Altp%C3%B6rtel_-_Blick_auf_Domfassade_und_Kircht%C3%BCrme_mit_Abendsonne.jpg";

	let meetups = [
		{
			id: "m1",
			title: "Coding Bootcamp",
			subtitle: "Learn to code in 2 minutes",
			description:
				"In this meetup, we will have some experts that teach you how to code in 2 hours",
			imageUrl:
				"https://upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Speyer_-_Altp%C3%B6rtel_-_Blick_auf_Domfassade_und_Kircht%C3%BCrme_mit_Abendsonne.jpg/750px-Speyer_-_Altp%C3%B6rtel_-_Blick_auf_Domfassade_und_Kircht%C3%BCrme_mit_Abendsonne.jpg",
			address: "Hyderabad, India",
			contactEmail: "dummy@email.com",
			isFavorite: false,
		},
		{
			id: "m2",
			title: "Svelte",
			subtitle: "Learn Svelte in 2 minutes",
			description:
				"In this meetup, we will have some experts that teach you Svelte in 2 hours",
			imageUrl: constImageUrl,
			address: "Hyderabad, India",
			contactEmail: "dummy@email.com",
			isFavorite: false,
		},
	];

	let editMode = null;

	const addMeetup = (e) => {
		const newMeetup = {
			id: Math.random().toString(),
			title: e.detail.title,
			subtitle: e.detail.subtitle,
			description: e.detail.description,
			contactEmail: e.detail.email,
			address: e.detail.address,
			imageUrl: constImageUrl, // e.detail.imageUrl,
			isFavorite: false,
		};
		meetups = [...meetups, newMeetup];
		editMode = null;
	};

	const toggleFavorite = (e) => {
		const id = e.detail;
		const updatedMeetup = { ...meetups.find((m) => m.id === id) };
		updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
		const updatedMeetupIndex = meetups.findIndex((m) => m.id === id);
		const updatedMeetups = [...meetups];
		updatedMeetups[updatedMeetupIndex] = updatedMeetup;
		meetups = updatedMeetups;
	};

	const cancelEdit = () => {
		editMode = null;
	};
</script>

<style>
	main {
		margin-top: 5rem;
	}

	.meetup-controls {
		margin: 1rem;
	}
</style>

<Header />
<main>
	<div class="meetup-controls">
		<Button
			on:click={() => {
				editMode = 'add';
			}}>
			New Meetup
		</Button>
	</div>
	{#if editMode === 'add'}
		<EditMeetup on:save={addMeetup} on:cancel={cancelEdit} />
	{/if}
	<MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>
