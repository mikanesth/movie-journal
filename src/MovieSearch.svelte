<script>
import { createEventDispatcher } from 'svelte';
let dispatch = createEventDispatcher();
let searchTerm ='';
const searchMovie = (st) => { 
    if(st){
        dispatch('searchedMovie', {
            searchTerm,
        });
    } else {
        dispatch('clearSearch', {});
    };
    }
</script>

<div class="searchbar">
    <input type="text" name="searchbar" id="searchbar" bind:value={searchTerm} on:keyup={searchMovie(searchTerm)}>
</div>


<style>

</style>