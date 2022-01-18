<script>
	import { createEventDispatcher } from 'svelte';
	import TextInput from '../UI/TextInput.svelte';
	import Button from '../UI/Button.svelte';
	import Modal from '../UI/Modal.svelte';

	let title = '';
	let subtitle = '';
	let address = '';
	let email = '';
	let description = '';
	let imageUrl = '';

	const dispatch = createEventDispatcher();

	const submitHandler = () => {
		dispatch('save', {
			title,
			subtitle,
			address,
			email,
			description,
			imageUrl,
		});
	};
</script>

<Modal on:cancel title="New Meetup">
	<form>
		<TextInput id="title" label="Title" value={title} on:input={(event) => (title = event.target.value)} />
		<TextInput
			id="subtitle"
			label="Subtitle"
			value={subtitle}
			on:input={(event) => (subtitle = event.target.value)}
		/>
		<TextInput id="address" label="Address" value={address} on:input={(event) => (address = event.target.value)} />
		<TextInput
			id="imageUrl"
			label="Image URL"
			value={imageUrl}
			on:input={(event) => (imageUrl = event.target.value)}
		/>
		<TextInput
			id="email"
			label="E-Mail"
			type="email"
			value={email}
			on:input={(event) => (email = event.target.value)}
		/>
		<TextInput
			id="description"
			label="Description"
			controlType="textarea"
			value={description}
			on:input={(event) => (description = event.target.value)}
		/>
	</form>
	<div slot="footer">
		<Button type="button" mode="outline" on:click={() => dispatch('cancel')}>Close</Button>
		<Button type="button" on:click={submitHandler}>Save</Button>
	</div>
</Modal>

<style>
	form {
		width: 30rem;
		max-width: 90%;
		margin: auto;
	}
</style>
