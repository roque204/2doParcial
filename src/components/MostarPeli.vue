<template>
    
</template>

<script>

export default {
  name: 'ApiPelicula',
}
//'/discover/movie?sort_by=popularity.desc&'
const API_KEY ='api_key=c493d2bdd674c2ddb0960c5301f4f6a1&language=es-MX';
const BASE_URL ='https://api.themoviedb.org/3';
const API_URL = BASE_URL + '/movie/popular?'
+API_KEY;
const IMG_URL = 'https://image.tmdb.org/t/p/w500';
const searchURL = BASE_URL + '/search/movie?'+API_KEY;

const main = document.getElementById('main');
const form = document.getElementById('form');
const search = document.getElementById('search');
getMovies(API_URL);

function getMovies(url){
    fetch(url).then(res => res.json()).then(data=>{
        
        console.log(data.results);
        showMovies(data.results);
    })
}

function showMovies(data){
    main.innerHTML = '';

    data.forEach(movie => {
        const {title, poster_path, overview, release_date, } = movie;
        const movieEl = document.createElement('div');
        movieEl.classList.add('movie');
        movieEl.innerHTML = `
        <img src="${IMG_URL+poster_path}" alt="${title}">

        <div class="movie-info">
            <h3>${title}</h3>
         
        </div>
        
        <div class="overview">
            <h3>${title}</h3> 
            <button v-on:click="agrFav(item)" type="button"> Agregar a Favpritos</button> <br> 
            ${overview}
            <br> <br> 
            <div> Fecha de lanzamiento: ${release_date} </div>
            <br> <br>
            
            
        

        </div>

        `

        main.appendChild(movieEl);
    })
}

function getColor(vote){
    if(vote>=7){
        return'green'
    }else if(vote>=5){
        return 'orage'
    }else{
        return 'red'
    }
}

form.addEventListener('submit',(e) =>{
    e.preventDefault();

    const searchTerm = search.value;

    if(searchTerm){
        getMovies(searchURL+'&query='+searchTerm)
    }

})

form.addEventListener('submit', (e) => {
    e.preventDefault();

    const searchTerm = search.value;
    const selectedYear = year.value;

    let url = searchURL;

    if (searchTerm) {
        url += '&query=' + searchTerm;
    }

    if (selectedYear) {
        url += '&year=' + selectedYear;
    }

    getMovies(url);
});

</script>

<style>


*{
    box-sizing: border-box;
}

:root{

    --primary-color:#141524;
    --secundary-color:#373b69;
}

body{
    background-color: var(--primary-color);
    font-family: 'Poppins', sans-serif;
    margin: 0;
   
}

.head{
    padding-top: 15px;
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 15vh;
    overflow: hidden;
}

header{
    
    background-color: var(--secundary-color);
    padding: 1rem;
    display: flex;
    justify-content: flex-end;

}

.search
{
    background-color: transparent;
    border: 2px solid var(--primary-color);
    padding: 0.5rem 1rem;
    border-radius: 50px;
    font-size: 1rem;
    color: #fff;
    font-family: inherit;
}

.search:focus{
    outline: 0;
    background-color: var(--primary-color);

}

.search::placeholder{
    color: #7378c5;
}

main{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.movie{
    width: 300px;
    margin: 1rem;
    border-radius: 3px;
    box-shadow: 0.2px 4px 5px rgba(red, green, blue, alpha);
    background-color: var(--secundary-color);
    position: relative;
    overflow: hidden;
}

.movie img {
    width: 100%;
    height: 350px; 
}

.movie-info{
    color: #eee;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5rem 1rem 1rem;
    letter-spacing: 0.5px;
}

.movie-info h3{
    margin-top: 0;

}

.movie-info span{
    background-color: var(--primary-color);
    padding: 0.25rem 0.5rem;
    font-weight: bold;
}



.overview{
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    background-color:#6a71c4;
    padding: 1rem;
    max-height: 100%;
    transform: translateY(140%);
    transition:transform 0.3s ease-in;
}

.movie:hover .overview{
    transform: translateY(0);
}

.titulo-tmdb{
    background-color: rgb(96, 153, 96);
}

</style> 