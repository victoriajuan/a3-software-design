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
    className: 'germany', // optional
    axes: [
      {axis: "strength", value: 13, yOffset: 10},
      {axis: "intelligence", value: 6},
      {axis: "charisma", value: 5},  
      {axis: "dexterity", value: 9},  
      {axis: "luck", value: 2, xOffset: -20}
    ]
  },
  {
    className: 'argentina',
    axes: [
      {axis: "strength", value: 6},
      {axis: "intelligence", value: 7},
      {axis: "charisma", value: 10},  
      {axis: "dexterity", value: 13},  
      {axis: "luck", value: 9}
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



