<template>
  <!-- <div id="chartdiv"></div> -->
  <div id="myDiv"><!-- Plotly chart will be drawn inside this DIV --></div>
</template>

<script src="https://cdn.plot.ly/plotly-2.11.1.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.17/d3.min.js"></script>
<script>
import * as am5 from "@amcharts/amcharts5";
// import * as am5xy from "@amcharts/amcharts5/xy";
import am5themes_Animated from "@amcharts/amcharts5/themes/Animated";

export default {
  mounted() {
    d3.csv(
      "https://raw.githubusercontent.com/plotly/datasets/master/2014_world_gdp_with_codes.csv",
      function (err, rows) {
        function unpack(rows, key) {
          return rows.map(function (row) {
            return row[key];
          });
        }

        var data = [
          {
            type: "choropleth",
            locations: unpack(rows, "CODE"),
            z: unpack(rows, "GDP (BILLIONS)"),
            text: unpack(rows, "COUNTRY"),
            colorscale: [
              [0, "rgb(5, 10, 172)"],
              [0.35, "rgb(40, 60, 190)"],
              [0.5, "rgb(70, 100, 245)"],
              [0.6, "rgb(90, 120, 245)"],
              [0.7, "rgb(106, 137, 247)"],
              [1, "rgb(220, 220, 220)"],
            ],
            autocolorscale: false,
            reversescale: true,
            marker: {
              line: {
                color: "rgb(180,180,180)",
                width: 0.5,
              },
            },
            tick0: 0,
            zmin: 0,
            dtick: 1000,
            colorbar: {
              autotic: false,
              tickprefix: "$",
              title: "GDP<br>Billions US$",
            },
          },
        ];

        var layout = {
          title:
            '2014 Global GDP<br>Source: <a href="https://www.cia.gov/library/publications/the-world-factbook/fields/2195.html"> CIA World Factbook</a>',
          geo: {
            showframe: false,
            showcoastlines: false,
            projection: {
              type: "mercator",
            },
          },
        };
        Plotly.newPlot("myDiv", data, layout, { showLink: false });
      }
    );
  },
};
</script>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}

#chartdiv {
  width: 100%;
  height: 500px;
  overflow: hidden;
}
</style>
