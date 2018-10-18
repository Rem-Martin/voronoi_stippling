// URL: https://beta.observablehq.com/d/804e38d4176df764
// Title: U.S. Airports Voronoi
// Author: rem-martin (@rem-martin)
// Version: 83
// Runtime version: 1

const m0 = {
  id: "804e38d4176df764@83",
  variables: [
    {
      inputs: ["md"],
      value: (function(md){return(
md`# U.S. Airports Voronoi

This [Voronoi diagram](https://github.com/Fil/d3-geo-voronoi) shows the region that is closest to each airport.`
)})
    },
    {
      name: "chart",
      inputs: ["d3","DOM","topojson","us","data","projection"],
      value: (function(d3,DOM,topojson,us,data,projection)
{
  const svg = d3.select(DOM.svg(960, 600))
      .style("width", "100%")
      .style("height", "auto");

  svg.append("path")
      .datum(topojson.merge(us, us.objects.states.geometries.filter(d => d.id !== "02" && d.id !== "15")))
      .attr("fill", "#ddd")
      .attr("d", d3.geoPath());

  svg.append("path")
      .datum(topojson.mesh(us, us.objects.states, (a, b) => a !== b))
      .attr("fill", "none")
      .attr("stroke", "white")
      .attr("stroke-linejoin", "round")
      .attr("d", d3.geoPath());

  svg.append("g")
      .attr("fill", "none")
      .attr("stroke", "red")
      .attr("pointer-events", "all")
    .selectAll("path")
    .data(d3.geoVoronoi().polygons(data).features)
    .enter().append("path")
      .attr("d", d3.geoPath(projection))
    .append("title")
      .text(d => {
        const p = d.properties.site.properties;
        return `${p.name} Airport
${p.city}, ${p.state}`;
      });

  svg.append("path")
      .datum({type: "FeatureCollection", features: data})
      .attr("d", d3.geoPath(projection).pointRadius(1.5));

  return svg.node();
}
)
    },
    {
      name: "data",
      inputs: ["d3"],
      value: (function(d3){return(
d3.csv("https://gist.githubusercontent.com"
    + "/mbostock/0fa5002fba21bc10e6126304c100c3ee"
    + "/raw/9a5c83dbe6d07911a29c345b5ac1f50ad73b0abd"
    + "/airports.csv", d => ({
  type: "Feature",
  properties: d,
  geometry: {
    type: "Point",
    coordinates: [+d.longitude, +d.latitude]
  }
}))
)})
    },
    {
      name: "projection",
      inputs: ["d3"],
      value: (function(d3){return(
d3.geoAlbers()
    .scale(1280)
    .translate([480, 300])
)})
    },
    {
      name: "us",
      inputs: ["d3"],
      value: (function(d3){return(
d3.json("https://unpkg.com/us-atlas@1/us/10m.json")
)})
    },
    {
      name: "topojson",
      inputs: ["require"],
      value: (function(require){return(
require("topojson-client@3")
)})
    },
    {
      name: "d3",
      inputs: ["require"],
      value: (function(require){return(
require("d3@5", "d3-geo-voronoi@1")
)})
    }
  ]
};

const notebook = {
  id: "804e38d4176df764@83",
  modules: [m0]
};

export default notebook;
