<script>
    export let movies;
</script>


<div class="movie-container">
{#each movies as movie (movie.title)}
<div class="movies">
    <h1>{movie.title.toUpperCase()}</h1>
    <p>Votre note est de: {movie.rating}</p>
</div>
{/each}
</div>


<style>
.movie-container {
    width: 100%;
    text-align: start;
    background: #ff3e00;
    color: white;
}
.movies {
    border-bottom: solid 2px white;
    width: 50%
}
</style>