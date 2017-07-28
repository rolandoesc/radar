# dbox-radar

A radar layer for [dbox](https://github.com/dboxjs/dbox).

## Example

```js
var visitors = [
  {"month": "Ene", "state": "Yucatán", "visitors": 121},
  {"month": "Feb", "state": "Yucatán", "visitors": 189},
  {"month": "Mar", "state": "Yucatán", "visitors": 123},
  {"month": "Abr", "state": "Yucatán", "visitors": 70},
  {"month": "May", "state": "Yucatán", "visitors": 40},
  {"month": "Ene", "state": "Quintana Roo", "visitors": 94},
  {"month": "Feb", "state": "Quintana Roo", "visitors": 125},
  {"month": "Mar", "state": "Quintana Roo", "visitors": 201},
  {"month": "Abr", "state": "Quintana Roo", "visitors": 229},
  {"month": "May", "state": "Quintana Roo", "visitors": 248},
  {"month": "Ene", "state": "Puebla", "visitors": 78},
  {"month": "Feb", "state": "Puebla", "visitors": 85},
  {"month": "Mar", "state": "Puebla", "visitors": 104},
  {"month": "Abr", "state": "Puebla", "visitors": 107},
  {"month": "May", "state": "Puebla", "visitors": 133},
  {"month": "Ene", "state": "San Luis Potosí", "visitors": 92},
  {"month": "Feb", "state": "San Luis Potosí", "visitors": 156},
  {"month": "Mar", "state": "San Luis Potosí", "visitors": 182},
  {"month": "Abr", "state": "San Luis Potosí", "visitors": 214},
  {"month": "May", "state": "San Luis Potosí", "visitors": 243}
];

var cfg = {
  bindTo: '#chart',
  size: {
    width: 800,
    height: 600,
    margin: {
      top: 40,
      bottom: 40,
      left: 30,
      right: 30
    },
  },
  data: {raw: visitors},
  legend: {
    enabled: true,
    at: {
      x: 600,
      y: 40
    }
  },
  axesFrom: 'month',
  polygonsFrom: 'state',
  valuesFrom: 'visitors',
  colors: ['red', 'yellow', 'green', 'blue'],
  ticks: 5,
  xAxis: {enabled: false},
  yAxis: {enabled: false},
  axisLabelMargin: 30
};

var chrt = dbox.chart(cfg)
  .layer(dbox.radar)
  .end()
  .draw();
```

## Configuration options

Sample data:

```json
[
  {"month": "Ene", "state": "Yucatán", "visitors": 421},
  {"month": "Feb", "state": "Yucatán", "visitors": 53},
  {"month": "Mar", "state": "Yucatán", "visitors": 28},
  {"month": "Ene", "state": "Quintana Roo", "visitors": 234},
  {"month": "Feb", "state": "Quintana Roo", "visitors": 198},
  {"month": "Mar", "state": "Quintana Roo", "visitors": 201},
  {"month": "Ene", "state": "Puebla", "visitors": 78},
  {"month": "Feb", "state": "Puebla", "visitors": 85},
  {"month": "Mar", "state": "Puebla", "visitors": 104},
  {"month": "Ene", "state": "San Luis Potosí", "visitors": 92},
  {"month": "Feb", "state": "San Luis Potosí", "visitors": 156},
  {"month": "Mar", "state": "San Luis Potosí ", "visitors": 182}
]
```

### legend.at

Default: `{x: 20, y: 20}`

Set the coordinates of the legend list. Set to an object with top and left properties indicating the position of the first legend, e.g., `{x: 40, y: 30}`.

### axesFrom

Required

What field to obtain the axes from, e.g., `'month'`.

### polygonsFrom

Required

What field to use to group the data in the chart's polygons representation, e.g., `'state'`.

### valuesFrom

Required

The field where values are found, e.g., `'visitors'`. This value is used to calculate the distance of the current record's point to the center of the chart.

### ticks

Default: `10`

Tell the underlying D3 scale how many ticks, i.e. circles, you *prefer* to be displayed (see [d3-scale](https://github.com/d3/d3-scale#continuous_ticks) for more details).

### transitionDuration

Default: `400`

Duration in milliseconds of the transitions of this chart. I you `filter()` then `draw()` an (already rendered) chart, this is the time the animation will take until getting to the chart's new visual state.

### axisLabelMargin

Default: `24`

How far each label will be from it's axis.
