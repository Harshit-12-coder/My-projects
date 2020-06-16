# TravelApp
Capstone of course Front End Developer - Udacity
By Harshit Adhikari

## Project Summary

    WHat we have  done here :
        * DOM / HTML / CSS - SASS
        * Retreive data from 3 APIs
        * Webpack environment
        * Express Server
        * Service Workers

## What You Will Build:

You will be building a travel application. It’s common to pull basic data from an API, but many applications don’t just pull the weather, they pull in multiple types of data, from different sources and **occasionally one API will be required to get data from another API.**

The project will include a simple form where you enter the location you are traveling to and the date you are leaving. If the trip is within a week, you will get the current weather forecast. If the trip is in the future, you will get a predicted forecast.The OpenWeather API is fantastic but it doesn’t let you get future data for free and it’s not that flexible with what information you enter; we are going to use the Weatherbit API for you to see how another API accomplishes the same goals. **Weatherbit API** has one problem, **it only takes in coordinates for weather data** -- it’s that specific. So, we’ll need to **get those coordinates from the Geonames API**. Once we have all of this data, we’ll want to **display an image of the location entered**; for this, we will be using the **Pixabay API**.

    Order:
        1. User Input travel location and date
        2. Get coordinates from the Geonames API
        3. Get weather data using the coordinates and using Weatherbit API -> If (date within a week) {gives the current weather forecast} Else {gives the predicted forecast}  (true/false)
        4. Display an image of the location entered using Pixabay API


        
# Getting Started

## Project Rubric
Your project will be evaluated by a Udacity code reviewer according to the Travel Planner App [project rubric](https://review.udacity.com/#!/rubrics/2669/view). Please review for detailed project requirements.

## Development Strategy

1. Start by duplicating your project 3 weather app. Once duplicated, change the new project’s name to make certain you're not overwriting your old project. We are going to build off this project as a foundation.


    2. Get webpack set up to work with this project. Use the skills you learned in project 4 to get your development environment going.
        * Create your src folder first. The src folder should contain a client folder and a server folder.

        * Your server folder should contain your server.js content.

        * Your client folder should contain a js folder, **media folder**, styles folder, and views folder, as well as an index.js file.

        * Your application js should go into the js file, your css into styles, and your index.html into views.

        * Convert your stylesheet from a .css file to a .scss file

        * Remember that webpack builds a dist file. You’ll need to **update your server js to access the dist folder.** (Hint: app.use(express.what goes here?))

        * Your **index.js file inside the client folder should import the main function of your application javascript, it should import your scss,** and it should export your main function from your application javascript. But in order to import, where will you need to **export it? -> library!**

        * *In project 4, you may have added your event listeners to the buttons themselves. For this project, you should be using .addEventListener(); If we are exporting functions from our application.js file, our event listeners can’t go there. Where can we put them? To call that exported function?*??
        
        * Now that your src folder is set up, it’s time to get webpack going. You should already have a few dependencies installed from project 3. **We need to add babel, babel loader, css loader, file loader, html loader, html webpack plugin, node sass, sass loader, style loader, webpack, webpack cli, and webpack dev server.** Refer to your project 4 to see what’s there, most of these should have been in use there.
        
        * Next, update the **scripts in package.json.** You will want to have **test, dev, start, and build.** NOTE: Start will be for your express server, dev will be so that you can take advantage of web dev server. It is possible depending on your setup to run both of these with one command.
        
        * Get your webpack config set up. Should be fairly similar to your language processing app webpack config. If you did not use webpack dev server in your language processing app, you will want to do so here. Additionally, **using source maps will help you debug your css.**
        To get webpack running, **you’ll want to first run npm run dev, then npm build to get your dist folder created. Once that is created you can run npm run dev and npm start simultaneously to have hot loading of your project as well as a working express environment.** NOTE: If needed, reference the stripped-down version of project 3 with webpack in the starter documentation.

    3. Create an account with [Geonames](http://www.geonames.org/export/web-services.html).

    4. Replace the openweather api with geonames api. *You already have one working api.* What information needs to get adjusted so that **instead of entering a zip code, you enter a city?** We want to get the **latitude, longitude, country,** instead of getting the temperature, feeling, and date.
        * *The weather data array was named differently, what do we need to change the name to?*??
        * *The weather data only had 1 object in the array, the geoname api outputs multiple objects. How do we call the first object?* ??

    5. Introduce a countdown. You’ll need to add a text field to your project to get the date.
        * What type of input should it be? *What about cross browser rendering?* ??
        * We’re looking to see how soon the trip is, how can you get the information from the DOM and see how soon that date is? -> .addEventListener()?
        * Where should you be storing that data once you have it?

    6. Create an account with [Weatherbit](https://www.weatherbit.io/account/create).

    7. Integrate the Weatherbit API similarly to how you integrated the geoname api. **What information needs to get adjusted for you to pull in the future weather?** *Getting a CORS error?* Check out this [article](https://medium.com/@dtkatz/3-ways-to-fix-the-cors-error-and-how-access-control-allow-origin-works-d97d55946d9) for some options. **NOTE: If you see that your app is working, but it takes several clicks to get all of the data,** think of why this could be. This is possibly the most challenging part of the project. **There is a major hint located in the Before you Begin section.** If you’re unable to figure it out, and your app still works with a few clicks, continue working on it, it may come to you later, or you’ll get guidance from your reviewer when you submit the app.
        * How does the Weatherbit API distinguish from the current forecast and future forecasts? **Does the API change in any way?**
        * How will we include the date? **What format does it need to be in?** How can we change it to the appropriate format?
    
    8. Create an account with [Pixabay](https://pixabay.com/api/docs/).
    
    9. Integrate the Pixabay API similarly to how you integrated the Geoname/Weatherbit APIs. What information are you going to submit to the API to achieve an appropriate image? **What if there are no results?**
        * What Parameters will you want to set to pull in images?
        * **How will you submit your data from the location field to a Pixabay URL parameter without having spaces in the url?** -> **Query string**
    
    10. Choose **one of the items from the suggested list to add in.** The items vary in complexity, but you must choose at least 1, all others are optional.
    
    11. REFACTOR. At this point, **your code should be working properly.** Ideally, refactoring happens while you are developing, but as a new developer, you often don’t have the whole picture in your head to be able to do so properly. Let’s clean the project up.
       Starting out it’s likely that you will have a globally scoped variables on occasion until you learn more about closures and design patterns. But **placing your code into functions is a great way to make your code more readable** and a way to avoid globally scoped variables.
        * Are your project files named in a way that makes sense?
        * **Add in services workers. Refer to project 4 for guidance.**

## Extend your Project Further - Roadmap/Strategy

**You'l need to implement at least one of the below in the project.** If you’re going to do any of the suggested tasks, *it’s recommended that you hold off on service workers until you are closer to submitting.* This is a good use for comments.

* Add end date and display length of trip. -> **Easiest!!**


## FEND Capstone - Travel App - Rubrics <https://review.udacity.com/#!/rubrics/2669/view>

### Architecture

- Root:
  - `package.json`
  - `readme.md`
  - `webpack.config.js`
  - src folder
    - server folder
      - `server.js` (name will vary)
    - client folder
      - `index.js`
      - html/views folder
        - `index.html`
      - js folder
        - `app.js` (name will vary)
      - styles folder
        - `style.scss` (name will vary - may be broke into partials)

### Testing

There should be at least one test for the express server and application javascript

### Visual Design

The design should clearly be different from the design used in projects 3 and 4.

### Server

*Server should be a near duplication of project 3 with the exception of additional added member: value pairs.*??

### index.js

    * At least one function should be imported.
    * At least one event listener should be imported.??
    * (styles referenced in html/css)

### Extend Options / Ways to Stand Out

At least one option from the Extend your Project/Ways to Stand Out sections have been added. Please add a Note to your reviewer which one you chose to implement, or add into your README.

* Add end date and display length of trip.

### Comments

Comments are present and effectively explain longer code procedure when necessary.

## Bibliography

* JEST Test's:
    * <https://zellwk.com/blog/endpoint-testing/>
    * <https://egghead.io/lessons/javascript-use-jest-s-interactive-watch-mode>
    * API Geoname API test example:
        * <https://github.com/StephanGeorg/geocoder-geonames/blob/master/test/geocoder-geonames.js>

* Service Worker API:
    * <https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API>

* API's used:
    * <http://www.geonames.org/export/web-services.html>
    * <https://www.weatherbit.io/account/create>
    * <https://pixabay.com/api/docs/>

* Error's:
    * Cors: <https://medium.com/@dtkatz/3-ways-to-fix-the-cors-error-and-how-access-control-allow-origin-works-d97d55946d9>

* JS tools:
    * Async: <https://zellwk.com/blog/async-await/>
    * Promises: <https://zellwk.com/blog/js-promises/>
    * Fetching: <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Fetching_data#Fetch>
    * CallBack Function: <https://developer.mozilla.org/en-US/docs/Glossary/Callback_function>
    * Query Strings: 
        * <https://www.youtube.com/watch?v=QTAYRmMsVCI>
        * <https://www.youtube.com/watch?v=zDovsTG2a7g>
        * <https://www.npmjs.com/package/query-string>
        * <https://www.devmedia.com.br/conceitos-e-exemplo-pratico-usando-querystring/18094>
        * <https://help.marklogic.com/Knowledgebase/Article/View/251/0/using-url-encoding-to-handle-special-characters-in-a-document-uri>
    * Arrow functions:
        * <https://www.youtube.com/watch?v=h33Srr5J9nY>
        * <https://www.youtube.com/watch?v=mrYMzpbFz18>
        * <https://www.youtube.com/watch?v=6sQDTgOqh-I&t=718s>
        * <https://www.youtube.com/watch?v=mrYMzpbFz18>
        * <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions>
    * Design Patterns:
        * <https://www.youtube.com/watch?v=1MxVA8y8IBA&list=PLAwxTw4SYaPkGKjpeiLWz8ydvFEkmRkBn>
        * <https://www.youtube.com/watch?v=BWprw8UHIzA>
        
## Conditions and documents of the APIs

### GeoNames

The parameter 'username' needs to be passed with each request. 
    
    username: notreal

Don't forget to url encode string parameters containing special characters or spaces.

    Examples:
    http://www.awebsite.com/encodingurls/submitmoviename.html?movie1=Fast+%26+Furious
    http://api.geonames.org/postalCodeLookupJSON?postalcode=6600&country=AT&username=demo

* Wikipedia Webservice (To put things more interest i can put another info for the API - opcional!)
    * The wikipedia webservices give access to georeferenced wikipedia articles in 240 languages

    Result : returns a list of wikipedia entries as xml document
    Example:
    http://api.geonames.org/findNearbyWikipedia?lat=47&lng=9&username=demo
    or
    api.geonames.org/findNearbyWikipedia?postalcode=8775&country=CH&radius=10&username=demo

* Use this url to get the lat and long

    Example : 
    http://api.geonames.org/searchJSON?q=london&maxRows=10&username=notreal

```
geonames: [
{
adminCode1: "ENG",
lng: "-0.12574",
geonameId: 2643743,
toponymName: "London",
countryId: "2635167",
fcl: "P",
population: 7556900,
countryCode: "GB",
name: "London",
fclName: "city, village,...",
adminCodes1: {
ISO3166_2: "ENG"
},
countryName: "India",
fcodeName: "A gold bird",
adminName1: "Harshit",
lat: "51.50853",
fcode: "PPLC"
}]
```

## Comunity help

Introducing data of coordinates to the weatherbit API, question:

    <https://hub.udacity.com/rooms/community:nd0011:906866-project-635-smg-2/community:thread-1ff72506-6edb-11ea-a3e5-eba2f058a289-3441456?messageId=3452832&contextType=room>

### API Geonames right url:

<https://knowledge.udacity.com/questions/116758>

    http://api.geonames.org/searchJSON?name=" +location+"&maxRows=1&username=" +username

    http://api.geonames.org/searchJSON?q=Paris&maxRows=10&username=notreal

### API Weatherbit

Great info to help understand API:
<https://www.weatherbit.io/api/swaggerui/weather-api-v2#/>

Request URL (16 day Forecast):

<https://api.weatherbit.io/v2.0/forecast/daily?lat=38.722252&lon=-9.139337&key=00000000000000000000000000>

API key = 00000000000000000000000000

### API Pixabay

<https://pixabay.com/api/docs/>

    Example, { KEY } must be your api key:
    <https://pixabay.com/api/?key={ KEY }&q=yellow+flowers&image_type=photo>

    Example with my API key
    <https://pixabay.com/api/?key=9999999999999999999999999999999&q=yellow+flowers&image_type=photo&pretty=true>

    Simplified:
    <https://pixabay.com/api/?key=99999999999999999999999999999999&q=yellow+flowers>
    
    "hits": [
    {
        "id": 195893,
        "pageURL": "https://pixabay.com/en/blossom-bloom-flower-195893/",
        "type": "photo",
        "tags": "blossom, bloom, flower",
        "previewURL": "https://cdn.pixabay.com/photo/2013/10/15/09/12/flower-195893_150.jpg"
        "previewWidth": 150,
        "previewHeight": 84,
        "webformatURL": "https://pixabay.com/get/35bbf209e13e39d2_640.jpg",
        "webformatWidth": 640,
        "webformatHeight": 360,
        "largeImageURL": "https://pixabay.com/get/ed6a99fd0a76647_1280.jpg",
        "user": "Yuri_B",
    }]
q:

A URL encoded search term. If omitted, all images are returned. This value may not exceed 100 characters.
Example: "yellow+flower"

webformatURL:

Medium sized image with a maximum width or height of 640 px (webformatWidth x webformatHeight). URL valid for 24 hours.

Replace '_640' in any webformatURL value to access other image sizes:
Replace with '_180' or '_340' to get a 180 or 340 px tall version of the image, respectively. Replace with '_960' to get the image in a maximum dimension of 960 x 720 px.

Your API key: 9999999999999999999999999999999999
Don't forget to figcapture the source:
* image: https://pixabay.com/
* user: Yuri_B

## Problems

### CORS

Usefull link:
<https://medium.com/@dtkatz/3-ways-to-fix-the-cors-error-and-how-access-control-allow-origin-works-d97d55946d9>

    const express = require('express');
        const request = require('request');
        

        const app = express();
        

        app.use((req, res, next) => {
        res.header('Access-Control-Allow-Origin', '*');
        next();
        });

### Event Listeners Imports

Usefull link:
<https://knowledge.udacity.com/questions/89677>

Instead of directly applying onclick event listener on the button like this:

    <button onclick="handleSubmit"> Submit <button/>

You just have to take care of following things:

You don't try to add the event listeners on the button before it is added to the DOM.
For this you can wrap all of your functionalities in a init() function which you'll call on DOMContentLoaded event. This will make sure your code is executed only after the DOM is ready.

### Recent Date

    let d = new Date();
    let newDate = d.getMonth()+'.'+ d.getDate()+'.'+ d.getFullYear();

# Tasks

- [x] Read geonames manual
- [x] Read Weatherbit 
- [x] Read Async info - take notes
- [x] Read jest and supertest - take notes
- [x] Read colegues questions on kwnoledge
- [x] Start by forking project weather api
- [x] Create a list of task in order to start project
- [x] Structure files project
- [x] .css to .scss
- [x] Update server to acess dist folder
- [x] import and export js and .scss
- [x] Webpack tools 
- [x] Update scripts package.json
- [x] Replace weather api to geonames api
- [x] integrate weatherbit api
- [x] integrate pixabay api
- [x] Get the server info the function updateUI
- [x] Create tag to change the UI
- [x] Change HTML & .scss to the input info (where? date of the travel? How much time)
- [x] Create regex to inputs
- [x] display the lenght of the travel HTML
- [x] Treat SCSS
- [x] Image background default
- [x] making test's
- [x] add Service Workers

