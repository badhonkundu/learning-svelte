<script>
	import ContactCard from "./ContactCard.svelte";

	let name = "";
	let title = "";
	let image = "";
	let description = "";
	let formState = "empty";
	let createdContacts = [];

	const addContact = () => {
		if (
			name.trim().length == 0 ||
			title.trim().length == 0 ||
			description.trim().length == 0 ||
			image.trim().length == 0
		) {
			formState = "invalid";
			return;
		}
		formState = "done";
		createdContacts = [
			...createdContacts,
			{
				id: Math.random(),
				name,
				jobTitle: title,
				imageUrl: image,
				desc: description,
			},
		];
	};

	const deleteFirst = () => {
		createdContacts = createdContacts.slice(1);
	}

	const deleteLast = () => {
		createdContacts = createdContacts.slice(0, -1);
	}
</script>

<style>
	#form {
		width: 30rem;
		max-width: 100%;
	}
</style>

<div id="form">
	<div class="form-control">
		<label for="userName">User Name</label>
		<input type="text" bind:value={name} id="userName" />
	</div>
	<div class="form-control">
		<label for="jobTitle">Job Title</label>
		<input type="text" bind:value={title} id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={image} id="image" />
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<textarea rows="3" bind:value={description} id="desc" />
	</div>
</div>

<button on:click={addContact}>Add Contact Card</button>
<button on:click={deleteFirst}>Delete first</button>
<button on:click={deleteLast}>Delete last</button>

{#if formState === 'invalid'}
	<p>invalid data</p>
{:else}
	<p>please enter some data before you submit</p>
{/if}

{#each createdContacts as contact, i (contact.id)}
	<h2># {i + 1}</h2>
	<ContactCard
		userName={contact.name}
		jobTitle={contact.jobTitle}
		description={contact.desc} />
{:else}
	<p>please start adding contacts. we found none!</p>
{/each}
