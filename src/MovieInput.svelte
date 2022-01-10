<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    let title = '';
    let rating = 1;
    function submitMovie(e){
        if(title){
            dispatch('submitedMovie', {
                movie: {
                    title,
                    rating,
                }
            });
            title='';
            rating=1;
        }
    }
</script>


<input type="text" placeholder="Movie Title" bind:value={title}/>

<select bind:value={rating} name="ratings" id="ratings">
    <option value={1}>1</option>
    <option value={2}>2</option>
    <option value={3}>3</option>
    <option value={4}>4</option>
    <option value={5}>5</option>
</select>

<button disabled={!title} on:click|preventDefault={submitMovie}>Add movie</button>



<style>

</style>