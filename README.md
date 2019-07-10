# Working with D3js

### General steps
1. dynamically append svg and g
```javascript
const svg = d3
  .select("body")
  .append("svg")
  .append("g")
```
2. Tree layout using d3.tree() and set the size
```javascript
const treeLayout = d3.tree().size([width, height]);
```
3. convert data using d3.hierarchy()
```javascript
const root = d3.hierarchy(data);
```
4. merge root with layout
```javascript
const treeData = treeLayout(root);

```
5. generate descendants
```javascript
const nodes = treeData.descendants();
```
6. selectAll then data
```javascript
const node = svg.selectAll("g.node").data(nodes);
```
7. append g
```javascript
const nodeEnter = node
  .enter()
  .append("g")
  .attr("class", "node");
```
8. append circle
```javascript
nodeEnter
  .append("circle")
  .attr("class", "node")
  .attr("cx", function(d) {
    return d.x;
  })
  .attr("cy", function(d) {
    return d.y;
  })
  .attr("r", 10)
  .style("fill", "lightsteelblue");
```