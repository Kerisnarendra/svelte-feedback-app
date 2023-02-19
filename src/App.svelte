<script>
	import FeedbackList from "./components/feedbackList.svelte";
	import FeedbackStas from "./components/FeedbackStas.svelte";
	import FeedbackForm from "./components/FeedbackForm.svelte";

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 2,
			rating: 9,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 3,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		}
	];
	$: count = feedback.length;
	$: average = feedback.reduce((a, {rating}) => a + rating, 0)/ feedback.length;

	const deleteFeedback = (e) => {
		const itemId = e.detail;

		feedback = feedback.filter((item) => item.id != itemId)
	}

	const addFeedback = (e) => {
		feedback = [e.detail, ...feedback]
	}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback}/>
	<FeedbackStas count={count} average={average}/>
	<FeedbackList feedback={feedback} on:delete-feedback={deleteFeedback}/>
</main>