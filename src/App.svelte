<script>
	import MovieInput from "./MovieInput.svelte";
	import MovieList from './MovieList.svelte';
	import MovieSearch from './MovieSearch.svelte';
	let moviesList = localStorage.getItem('moviesList') ? JSON.parse(localStorage.getItem('moviesList')) : [];
	function saveMovie(movie){
		const updatedMovie = [...moviesList, movie];
		localStorage.setItem('moviesList', JSON.stringify(updatedMovie));
		moviesList = updatedMovie;
	}
	function filterMovies(st){
		let updatedMoviesList = moviesList.filter(m => m.title.toLowerCase().includes(st.searchTerm.toLowerCase()));
		moviesList = updatedMoviesList;	
	}

	function clearSearched(e){
		moviesList = localStorage.getItem('moviesList') ? JSON.parse(localStorage.getItem('moviesList')) : [];
	}


</script>

<div class="main">
	<h1>movie journal</h1>
</div>

<MovieSearch on:searchedMovie={e => {filterMovies(e.detail)}} on:clearSearch={clearSearched} />

<MovieInput on:submitedMovie={e => {saveMovie(e.detail.movie)}}/>

<MovieList movies={moviesList}/>

<style>
	.main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
</style>