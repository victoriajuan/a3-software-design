# a3-software-design

A radar chart can be reuse by different dataset and other use controling factors.

## Files

- **`radar.js`** : a JavaScript file contains the function for rendering reuseable radar chart.
- **`main.css`** : stylesheet containing more style for components.

## Functionalities

- **`components`** : Create main radar chart components includes `allAxis`, `totalAxes`, `radius` of chart, `verticesTooltip`, numbers of `level` of chart, `axes`, `vertices`, `legend`

- **`coordinates`** : build [x, y] corrdinates of polygon vertices in the svg area, it can be adjusted based on the user input value of width and height

- **`level`** : build out the levels of spiderweb, it can also be adjusted based on the user input value of width and height

- **`level label`** : build out the levels labels for each level

- **`axes`** : build out axes of the spiderweb, the number of them based on the data mapping result

- **`axes label`** : build out the axes labels

- **`legend`** : build out the legend to represent the chart variables

- **`vertices`** : build out the polygon vertices of the dataset, closer to the middle the smaller value a vertice gets

- **`polygons`** : build out the polygon areas of the dataset based on the data value of each vertices, it's the main part of data representing/visualization of the radar chart

- **`show tooltip`** & **`hide tooltip`** : show and hide the tolltip information text when hover in or hover out

## Inputs

- **`level`** : user can adjust how many level of the spiderweb they want for the radar chart

- **`width`** : user can adjust the svg's width to adjust the size of the radar chart

- **`height`** : user can adjust the svg's height to adjust the size of the radar chart

- **`labelScale`** : user can adjust the scale of label to adjust the size of the labels in radar chart

- **`legendBoxSize`** : user can adjust the size of the legend box based on their own need

- **`color`** : user can adjust the color which will apply to `vertices`, `polygons` and `legends`' color. `It will not change the color of level, axes, level labels and axes labels`.

## Instruction

- To start using this reuseable d3 chart type, the user need to have their data, but in our format and variable names. The data will look similar to this example .csv file.

```js
data_the_avengers.csv#

group, axis, value, description
Captain America, Intelligence, 3, only human
Captain America, Strength, 3,  only human
Captain America, Speed, 2,  only human
Captain America, Durability, 3,  only human
Captain America, Energy, 1,  only human
Captain America, Fighting Skills, 6, able to judge combat decisively 
Iron Man, Intelligence, 6, Smart entreprenuer
Iron Man, Strength, 6, Powered by his suit
Iron Man, Speed, 5, rocket boosters
Iron Man, Durability, 6, tough durable material
Iron Man, Energy, 6, 
Iron Man, Fighting Skills, 4, 
Hulk, Intelligence, 6, Scientist brilliance
Hulk, Strength, 7, Insanely strong
Hulk, Speed, 3, clumsy
Hulk, Durability, 7, Close to industructible
Hulk, Energy, 1, 
Hulk, Fighting Skills, 4, great at SMASHING
Thor, Intelligence, 2, not too bright
Thor, Strength, 7, god-like strength
Thor, Speed, 7, god-like speed
Thor, Durability, 6, god-like durability
Thor, Energy, 6, 
Thor, Fighting Skills, 4, quite low for a god???

```

**`data structure`**

```js
var data = [
  {
    className: 'Captain America', // optional
    axes: [
      {axis: "Intelligence", value: 33, description: "only human"},
      {axis: "Strength", value: 3, description: "only human"},
      {axis: "Speed", value: 2, description: "only human"},  
      {axis: "Durability", value: 3, description: "only human"},  
      {axis: "Energy", value: 1, description: "only human"},
      {axis: "Fighting Skills", value: 1, description: "able to judge combat decisively"}
    ]
  },
  {
    className: 'Iron Man',
    axes: [
      {axis: "Intelligence", value: 6, description: "Smart entreprenuer"},
      {axis: "Strength", value: 6, description: "Powered by his suit"},
      {axis: "Speed", value: 5. description: "rocket boosters"},  
      {axis: "Durability", value: 6, description: "tough durable material"},  
      {axis: "Energy", value: 6, description: },
      {axis: "Fighting Skills", value: 4, description: }
    ]
  },
  {
    className: 'Hulk',
    axes: [
      {axis: "Intelligence", value: 6, description: "Scientist brilliance"},
      {axis: "Strength", value: 7, description: "Insanely strong"},
      {axis: "Speed", value: 3. description: "clumsy"},  
      {axis: "Durability", value: 7, description: "Close to industructible"},  
      {axis: "Energy", value: 1, description: },
      {axis: "Fighting Skills", value: 4, description: "great at SMASHING"}
    ]
  },
  {
    className: 'Thor',
    axes: [
      {axis: "Intelligence", value: 2, description: "not too bright"},
      {axis: "Strength", value: 7, description: "god-like strength"},
      {axis: "Speed", value: 7. description: "god-like speed"},  
      {axis: "Durability", value: 6, description: "god-like durability"},  
      {axis: "Energy", value: 6, description: },
      {axis: "Fighting Skills", value: 4, description: "quite low for a god???"}
    ]
  }
];
```
- Once you have your dataset, you should be able to render the chart on different data using this approach:

```js
var myChart = radar().param1(value1).param2(value2);

var chartWrapper = d3.select('#my-div')
                .datum([dataSet]) 
                .call(myChart);
```

- Internally, the software supports the smooth updating of data and / parameters using this method

```js
// Initiation of chart
var chartWrapper = d3.select('#my-div').datum([dataSet]).call(myChart); 

// Update a chart parameter and the data (on some event handler)
myChart.param1(newValue);
chartWrapper.datum([newDataSet]).call(myChart);
```



