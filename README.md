# Project 2: Movie-Tracker

![Screenshot1](./public/images/gif.gif)

## Summary:
With the usage of Javascript, Movie-Tracker is an application that keeps a record of movies individual users have added to their wishlist. It also tracks the movies they have watched, categorizing them into ‘liked’ and ‘disliked’ columns. Given the amount of movies out there, old, current and upcoming movies, Movie-Tracker provides an easy solution for users to keep a tabs on the movies they have seen, is out currently and wish to see in the future. By liking or disliking movies by users will give them more functionality--try it out and track some movies you personally desire!

## Demo link:
https://sleepy-lowlands-10803.herokuapp.com/

## File Structure:
![](public/images/file-structure.png)

## Getting Started:
The simpliest way in seeing a demo of Movie-Tracker is to click on the Heroku demo link right above that leads it directly to the project without any installations required. This link can be found within this readme file or at the description area within http://github.com/duongsters/movie-tracker

To connect locally...
1) Clone Movie-Tracker repository via https://github.com/duongsters/movie-tracker
2) Run command line Terminal (or via Gitbash) 'npm install' for required NPMS used within the application...or just download all NPMs from Technologies Used below.
3) Run command line 'node server.js' to start up the application
4) Once connected to http://localhost:8080/ from CLI, copy that exact link to URL
5) Run 'ctrl + c' within the CLI to exit the application entirely


## Technologies Used:
- Javascript
- .JS: node.JS, particles.JS, express.JS, sequelize.JS
- CSS: animate.css
- jQuery
- NPM: Express, MySql, Sequelize, Path, body-parser, Heroku
- API: OMDB
- Bootstrap
- WebKit
- Iconify

## Code Snippets:
via wishlist.js:
* The 'displayMovieInfo' function runs initially by creating an AJAX call for the specific movie button being clicked...then iterates through response array to get movie ids with the for-loop. After, it will run the 'getMovieData' function to get the full movie info
```javascript
    function displayMovieInfo() {
        var movie = $("#movie-input").val();
        var queryURL = "https://www.omdbapi.com/?s=" + movie + "&y=&plot=short&apikey=9e558ee4";

        $.ajax({
            url: queryURL,
            method: "GET"
        }).then(function (response) {
            $(".container-movies").empty();
            for (var i = 0; i < response.Search.length; i++) {
                getMovieData(response.Search[i].imdbID);
            }
        });
    }
```
via wishlist.js:
* The 'getMovieData' function runs to get full movie info by searching for the movie id, the 'omdbID', the runs the 'createMovieElement' function to fill the page
```javascript
    function getMovieData(movieId) {
        var queryURL = "https://www.omdbapi.com/?i=" + movieId + "&y=&plot=short&apikey=9e558ee4"
        $.ajax({
            url: queryURL,
            method: "GET"
        }).then(function (response) {
            createMovieElement(response);
        })
    }
```

via wishlist.js:
* This important function, 'createMovieElement', will take all the needed information from OMDB's API server then dynamically generated the movie results within the wishlist.html webpage
```javascript
function createMovieElement(response) {
    var resultsFront = $("<div class='movie-inside front'>");
    var resultsBack = $("<div class='movie-inside back'>");
    var movieDetails = $("<div class='movie-details'>");
    var movieBox = $("<div class='movie'>");
    var movieContainer = $("<div class='container-movie'>");


    var addToWishlist = $("<button class='addToWishlist' type='button'>Add to Wishlist</button>");
    addToWishlist.data("id", response.imdbID);

    var poster = response.Poster;
    var posterInput = $("<img class='movie-poster'>").attr("src", poster);
    resultsFront.append(posterInput);

    var title = response.Title;
    var titleInput = $("<h1 class='movie-title'>").text(title);
    movieDetails.append(titleInput);


    var year = response.Year;
    var yearInput = $("<span>").text("Released: " + year);
    movieDetails.append(yearInput);



    var runtime = response.Runtime;
    var runtimeInput = $("<span>").text(" Runtime: " + runtime);
    movieDetails.append(runtimeInput);


    var plot = response.Plot;
    var plotInput = $("<p class='movie-plot'>").text("Plot: " + plot);
    movieDetails.append(plotInput);


    movieBox.append(resultsFront);
    resultsBack.append(movieDetails);
    movieBox.append(resultsBack);


    resultsBack.append(addToWishlist);

    movieContainer.append(movieBox);

    $(".container-movies").append(movieContainer);
}
```

# Author Links:

## Andrew
- [GitHub](https://github.com/duongsters) ||
 [LinkIn](https://www.linkedin.com/in/theandrewduong/) ||
 [Portfolio](https://www.duongsters.github.io/updated-portfolio/)

#### Responsible for:
- [server](https://github.com/duongsters/movie-tracker/blob/master/server.js)
- [public (wishlist.html)](https://github.com/duongsters/movie-tracker/blob/master/server.js)
- [public/js (wishlist.js)](https://github.com/duongsters/movie-tracker/blob/master/public/js/wishlist.js)
- [public/css (styles.css)](https://github.com/duongsters/movie-tracker/blob/master/public/css/styles.css)

### Oliver Sun
- [GitHub](https://github.com/Olisun?tab=repositories) ||
 [LinkIn](https://www.linkedin.com/in/oliver-sun-4b6baba/)
#### Responsible for: 
- [routes](https://github.com/duongsters/movie-tracker/tree/master/routes)
- [schema](https://github.com/duongsters/movie-tracker/tree/master/schema)
- [public/css (style.css)](https://github.com/duongsters/movie-tracker/blob/master/public/css/style.css)
- [config](https://github.com/duongsters/movie-tracker/tree/master/config)
- [public (user.html)](https://github.com/duongsters/movie-tracker/blob/master/public/user.html)
- [models (index.js)](https://github.com/duongsters/movie-tracker/blob/master/models/index.js)
- [public/js (particles.js)](https://github.com/duongsters/movie-tracker/blob/master/public/js/particles.js)


### Jordan Hagood
- [GitHub](https://github.com/hagoodj) ||
 [LinkIn](https://www.linkedin.com/in/jordan-hagood-7b306410b/)
#### Responsible for:
- [models](https://github.com/duongsters/movie-tracker/tree/master/models)
- [public/js (movietracker.js, wishlist.js)](https://github.com/duongsters/movie-tracker/tree/master/public/js)
- [public (wishlist.html)](https://github.com/duongsters/movie-tracker/blob/master/public/wishlist.html)

