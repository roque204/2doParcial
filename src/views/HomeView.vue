<template>

  <div class="home">
    <favoritos>
    <h1 class="titulo-tmdb">Favoritos TMDB </h1>
    <div v-for='item in fav' v-bind:key="item.id">
                <h3>{{item.title}}</h3>
                <h4>{{item.precio}}</h4>
    </div>
    </favoritos>
    


    <main id="main">
        <div class="movie">
             
        </div>  
        
    </main>


  </div>

  

</template>

<script>
// @ is an alias to /src
import favoritos from '@/components/Favoritos.vue'


export default {
  name: 'Favoritos',
  components: {
    favoritos,
  }
}

</script>


<style>


*{
    box-sizing: border-box;
}

:root{

    --primary-color:#22254b;
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

.movie-info span.green{
    color: rgb(7, 245, 7);
}

.movie-info span.orange{
    color: rgb(255, 153, 0);
}

.movie-info span.red{
    color: red;
}

.overview{
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #fff;
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
