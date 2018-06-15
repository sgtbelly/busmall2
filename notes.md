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

/////////// Avocado demo ///////////////////////////

/////// html ///////
<body>
  <main>
      <section>
          <h1>Choose the ripest avacado</h1>
      </section>
      <section id="display">
            <img src="" class="img1"/>
            <img src="" class="img2"/>
      </section>
      <div>
          <button id="button">Show Results</button>
      </div>
      <section id="chart-section">
          <canvas id="canvas" width="300" height="300"></canvas>
      </section>
  </main>
</body>

//// Java Script /////
//****DATA****//

var allAvocados = [];

//****CONSTRUCTOR & INSTANCES****//

function Avocado(name, path, shown, votes) {
  this.name = name;
  this.path = path;
  this.timesShown = shown;
  this.votes = votes;
  allAvocados.push(this);
}

function instantiateAvocados() {
  var hand = new Avocado("hand", "img/avocado-hand.png", 0, 0);
  var cartoon = new Avocado("cartoon", "img/avoCartoon.jpg", 0, 0);
  var hass = new Avocado("hass", "img/hass.jpg", 0, 0);
  var ripe = new Avocado("ripe", "img/ripe-avocado.png", 0, 0);
  var bird = new Avocado("bird", "img/avocado-bird.jpg", 0, 0);
}

//****IMAGE & VOTING FUNCTIONS****//

var tracker = {
  chartLabels: [],
  chartVotes: [],
  img1: document.getElementsByClassName("img1")[0], //Elements by Class Name! 
  img2: document.getElementsByClassName("img2")[0],
  displaySection: document.getElementById("display"),
  resultsButton: document.getElementById("button"),

  // now need a way to randomize the images
  randomIndex: function(arr) {
    return Math.floor(Math.random() * arr.length);
  },

  getIndices: function(arr) {
    var ind1 = this.randomIndex(arr);
    var ind2 = this.randomIndex(arr);
    // to prevent two of the same images at the same time
    while (ind1 === ind2) {
      ind2 = this.randomIndex(arr);
    }
    // return the array with our randomize index places
    return [ind1, ind2];
  },

  displayPics: function() {
    var indices = this.getIndices(allAvocados);
    var leftImg = allAvocados[indices[0]];
    var rightImg = allAvocados[indices[1]];

    this.img1.src = leftImg.path;
    this.img2.src = rightImg.path;

    this.img1.id = leftImg.name;
    this.img2.id = rightImg.name;

//count for how many times each image was shown

    leftImg.timesShown += 1;
    rightImg.timesShown += 1;
  },

// some 301 concepts

  tallyVote: function(id) {
    for (var avo of allAvocados) {
      if (avo.name === id) {
        avo.votes += 1;
      }
    }

//saving to local storage

    var strAvocados = JSON.stringify(allAvocados);
    localStorage.setItem("avocados", strAvocados);
  },

  //****CHART FUNCTIONS****//

  updateChartData: function() {
    for (var i = 0; i < allAvocados.length; i++) {
      this.chartLabels[i] = allAvocados[i].name;
      this.chartVotes[i] = allAvocados[i].votes;
    }
  },

  makeChart: function() {
    var canvas = document.getElementById("canvas");
    var ctx = canvas.getContext("2d");

    tracker.updateChartData();

    var chart = new Chart(ctx, {
      type: "bar",
      data: {
        labels: tracker.chartLabels,
        datasets: [
          {
            label: "Votes",
            backgroundColor: "rgba(255,99,132,0.2)",
            borderColor: "rgba(255,99,132,1)",
            borderWidth: 1,
            hoverBackgroundColor: "rgba(255,99,132,0.4)",
            hoverBorderColor: "rgba(255,99,132,1)",
            data: tracker.chartVotes
          }
        ]
      }
    });
  }
};

//****EVENT LISTENERS****//

tracker.displaySection.addEventListener("click", function(event) {
  if (event.target.id !== "display") {
    tracker.tallyVote(event.target.id);
    tracker.displayPics();
  }
});

tracker.resultsButton.addEventListener("click", tracker.makeChart);

//****GET AVOCADOS FROM LOCALSTORAGE****//
//IIFE immediately invoved function expression

(function getLocalStorage() {
  if (localStorage.avocados) {
    var strAvocados = localStorage.getItem("avocados");
    var avocados = JSON.parse(strAvocados);
    console.log(avocados);
    for (var avo of avocados) {
      console.log(avo);
      var newAvo = new Avocado(avo.name, avo.path, avo.timesShown, avo.votes);
    }
  } else {
    instantiateAvocados();
  }
})();

//****SHOW FIRST PICS****//

tracker.displayPics();

//css

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#display {
  display: flex;
  justify:
}

/////// cart.js demo //////////
'use strict';

//global vars
var btn = document.getElementById('btn'); // button
var input = document.getElementById('item');
var tasks = document.getElementById('tasks');

//need a way to save the inputadd it to local storage
//create li element for the input 
//need an event to add the tasks to the list
//DOM manipulation within the elements 

//conditional that asks is there a property currently on localStorage that is a list? Does it have a value equal to ''?
//split will coerce it back into an array and get rid of the comma
//else we will take out the comma and set up an empty array that we can fill

if(localStorage.list) {
    var list = localStorage.list.split(',');
} else {
    var list = [];
}

//save the state of our application
//attach it to some sort of event listener
//grab our list and push the value of what of what we type in to localStorage
//every time you add an item your item will go to localStorage

function save() {
    list.push(input.value);
    localStorage.list = list;
    // meta data so you can see what is happening in action
    console.log('list arr:', list);
    console.log('localStorage list:', localStorage.list);
}

//modularizing code
//make naming conventions that are easy to read
// a function to manipulate and create a list

function create() {
    var val = input.value;
    //creating the item so getting the value of the input
    var item = document.createElement('li');
    //each individual item
    //do what to the li? Put stuff in it that is coming from val
    //in the past we've used innerHTML or text content..this is NEW
    //.createTextNode will solve problems in the future trust me
    //just appending child text specifically to just an element in memory. Putting nothing but text

    item.appendChild(document.createTextNode(val));
    //need to take our tasks which is our ul and append child with the added li we just created
    tasks.appendChild(item);
    //each time you press enter you get a new empty value to enter a new val
    input.value = '';
}
    //load it out of localStorage
    //if list has data in it, has a value it will run
    //will say truthy or falsey based on what is in it. You don't need === or !==

function load() {
    if(localStorage.list) {
        //set up an item so we can deal with our for loop
        //creating an arbitrary loop starting at zero and incrementing up through the array
        var item; 
        for (var x = 0; x < list.length; x++) {
            item = document.createElement('li');
            //stuff text into the li
            //list to the x will have all of our text in it
            item.appendChild(document.createTextNode(list[x]));

            tasks.appendChild(item);
        }
    }
}

//wrap a bunch of function calls and call them in one function
//anytime we click on a button we call render

function render() {
    save();
    create();
}

load();

btn.addEventListener('click', render);

// forEach list item in cart.