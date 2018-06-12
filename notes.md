# busmall pseudocode
- create the repo
- create the md file for the user stories
- wireframe it and break it down, visualize 
- import images 
- display 3 random images from the assets
- give user 25 clicks
- choose one of the random images
- keep track of the number of times an image was clicked
- keep track of the number of times an image was displayed
- print out a report of data at the end
- need a way to represent an image
- in order to display an image what do we need to be able to do? 
- need a source...and an image element
- constructor function something like Photo 
- also need # of votes or selections.
- consider starting at 25 and working down
- chart.js is an object literal
////////////////////////// Demo Code ////////////////////////////////////////////////////

'use strict'

//array to store objects

Goat.allGoats = []

//constructor function

function Goat(name, filepath) {
this.name = name;
this.filepath = filepath;
Goats.allGoats.push(this)
}

//use constructor to create new goat pics

new Goat('Crusin goat', 'img/cruisin-goat.jpg');
new Goat('kissing goat', 'img/kissing-goat.jpg');
new Goat('sassy goat' , 'img/sassy-goat.jpg');

//listen for those events, something to be clicked all about events

var imgEL = document.getElementById('goat-pic');
imgEl.addEventListner('click', randomGoat);

//randomly display one of the pics

function randomGoat() {
var randomIndex = Math.floor(Math.random() * goat.allGoats.length)
imgEL.src = Goats.allGoats[randomIndex].filepath;
}

// counter

////////////////////// CSS Demo //////////////////////////////////////////////////
border: 2px, solid: yellow;

//////////////////////////////// Local Storage Demo Code //////////////////////////////////
# Local Storage
- find it in aplications in your browser
- storage API (object)
- key = stored data 
- value = object
- you can use local or session storage
- local = come back after closing broswer
- session = will not come back after closing browser
- jsonlint.com go here to validate json.lint
- json encoding (trns it into a stream) and decoding (when we read it "parse") 
- json is an built in javascript object

var obj = {a: 0, b: 1, c: 2}

JSON.string(obj)
"{"a":0, "b":1, "c":2}"
//encoded now

var jsonObj = JSON.stringify(obj);
jsonObj
"{"a":0, "b":1, "c":2}"

JSON.parse(jsonObj);
{a: 0, b: 1, c: 2}
//turns it back to regular JS

obj
{a:}

// when we encode into JSON then parse it it comes back different.

var jsonStudent2 = JSON.stringify(student2)
//four steps in local storage to remeber
- take setItem method to put into localStorage
    1. JSON.strignify()
    2. localstorage.setItem()
- first two are encoding it or setting it in the database
- last two steps are retriving it from the built in database and turining it back into JS (but taking up different space in memory thaough it looks the same)
    3. localstorage.getItem()
    4. JSON .parse()

pgs 421-422 local storage API

clear local storage
<button id="clearstorage">Clear Local Stroage<>

//stringify all the things
//localstorage.setitem();
//add all the things that you need in busmall? votes names clicks views
//our stuff in local storage will be in JSON and not only JSON but stringified JSON

var john = { 
  name = 'john';
  instructor: true;
  favNumShots: 6,
  willLaugh: function() {
    alert('hahahaha');

  }
};

var raychill = ['racheal', true];
var anotherAray = ['random', 9, false, raychill];
var clearLS = document.getElementById('clearStorage')
