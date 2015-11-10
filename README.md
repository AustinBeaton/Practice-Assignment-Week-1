# Practice-Assignment-Week-1
<!DOCTYPE HTML>
<html>
	<head>
		<meta name="viewport" content="initial-scale=1.0, user-scalable=no">
		<meta http-equiv="content-type" content="text/html; charset=UTF-8">
		<title></title>
		<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.in.js"></script>
		<script type="text/javascript" src="http://d3js.org/d3.v3.js"></script>
		<style>

			body {
				font: 10px sans-serif;
			}
				.chart {
					font-family: Impact, sans-serif;
					font-size: 8px;
				}
				.axis path, .axis line {
					fill: none;
					stroke: #0000ff;
					stroke-width: 1px;
					shape-rendering: softEdges;
				}
				.bar {
					fill: red;
					z-index: 1000;
				}
				.grid .tick {
				stroke: lightgrey;
				opacity: 2.0;
				z-index: -1000;
				
}
		</style>
		<script type="text/javascript">
			$(document).ready(function(){
				var data = [{"month": "January","total":11},{"month":"February","total":14},{"month":"March","total": 18},{"month":"April","total":23},{"month":"May","total":27},{"month":"June","total":30},{"month":"July","total":32},{"month":"August","total":31},{"month":"September","total":28}, {"month":"October","total":23},{"month":"November","total":18},{"month":"December","total":12}];
				var margin = {top: 40, right: 40, bottom: 40, left:40}, width = 1200, height = 1000; 
				var x = d3.time.scale().domain([new Date(data[0].date), d3.month.offset(new Date(data[data.length - 1].date), 1)]).rangeRound([0, width - margin.left - margin.right]);
				var y = d3.scale.linear().domain([0, d3.max(data, function(d) {return d.total;})]).range([height - margin.top - margin.bottom, 0]);
				var xAxis = d3.svg.axis()
					.scale(x)
					.orient('bottom')
					.ticks(d3.time.days, 1)
					.tickFormat(d3.time.format(%m-%d-%Y'))
					.tickSize(0)
					.tickPadding(20);
				var yAxis = d3.svg.axis()
					.scale(y)
					.orient('left')
					.tickPadding(8);
				var xAxis1 = d3.svg.axis()
					.scale(x)
					.orent('bottom');
				var yAxis1 = d3.svg.axis()
					.scale(y)
					.orient('left');
				var svg = d3.select('#bar-demo').append('svg')
					.attr('class','chart')
					.attr('height',height)
					.append('transform','translate('+ margin.left + ',' +margin.top + ')');
				
				svg.append("g")
					.attr("class","grid")
					.attr("transform","translate(0, "height - margin.bottom - margin.top)+")")
					.call(xAxis1)
					.ticks(d3.time.hours, 12) 
					.tickSize(-(height-margin.top-margin,bottom), 0,0)
					.tickFormat(""));
				svg.append('g')
					.attr('class', 'axis')
					.attr('transform', 'translate(0, '+height - margin.top - margin.bottom) +')')
					.call(yAxis);
				svg.append('g')
					.attr('class', 'axis')
					.call(yAxis);
				svg.append("g")
					.attr("class", "grid")
					.call(yAxis1
					.ticks(20));
					.tickSize (-(width-margin.left-margin.right), 0, 0)
					.tcikFormat(""));
				svg.selectAll('.chart')
					.data(data)
					.enter()
					.append('rect')
					.attr('class', 'bar')
					.attr('x', function(d) { return x(new Date(d.month)); })
					.attr('y', function(d) { return height - margin.top - margin.bottom - (height - margin.top - margin.bottom - y(d.total)) })
					.attr('width', 25)
					.attr('height', function(d) {return height - margin.top - margin.bottom - y(d.total) });
				svg.selectAll(".rect")
					.data(data)
					.enter().append("svg:text")
					.attr("x", function(d) { return x(new Date(d.month));})
					.attr("y", function(d) {return y(d.total); })
					.attr("dx", "0.5em")
					.attr("dy", "1.50em")
					.attr("text-anchor", "left")
					.text(function(d) {return d.total });
				svg.append("text")
					.attr("x", (width/ 2))
					.attr("y", 0 - (margin.top/ 2))
					.attr("text-anchor","middle")
					.style("font-size", "20px")
					.text("Average Daily High(°C) by Month - Atlanta, Georgia") });		
		</script>
	</head>
	<body>
		<div id="bar-demo" style="position: relative; top: 3px; left: 20px;">
		<svg class="chart" width="1200" height="500"><g transform="translate(40, 40)">
			<g class="grid" transform="translate(0,420)"><g class="tick" transform="translate(15,0)" style="opacity: 1;">
			<line y2="-420" x2="0"></line><text dy=".71em" y="3" x="0" style="text-anchor: end;">
			</text></g>
			<g class="tick" transform="translate(53,0)" style="opacity: 1;">
				<line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(90,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(127,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(164,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(201,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(238,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(275,0)" style="opacity: 1;"><line y2="-420" x2="0"></line
				><text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(313,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(350,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(387,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(424,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(461,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(498,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(535,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(572,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(609,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(646,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(683,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(720,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(757,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(794,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(831,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
			<g class="tick" transform="translate(868,0)" style="opacity: 1;"><line y2="-420" x2="0"></line>
				<text dy=".71em" y="3" x="0" style="text-anchor: middle;"></text></g>
		<path class="domain" d="M0,0V0H520V0"></path></g>
			<g class="axis" transform="translate(0, 420)"><g class="tick" transform="translate(15,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">January</text></g>
			<g class="tick" transform="translate(90,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">February</text></g>
			<g class="tick" transform="translate(164,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">March</text></g>
			<g class="tick" transform="translate(238,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">April</text></g>
			<g class="tick" transform="translate(313,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">May</text></g>
			<g class="tick" transform="translate(387,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">June</text></g>
			<g class="tick" transform="translate(461,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">July</text></g>
			<g class="tick" transform="translate(535,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">August</text></g>
			<g class="tick" transform="translate(609,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">September</text></g>
			<g class="tick" transform="translate(683,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">October</text></g>
			<g class="tick" transform="translate(757,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">November</text></g>
			<g class="tick" transform="translate(831,0)" style="opacity: 1;"><line y2="0" x2="0"></line>
				<text dy=".71em" y="8" x="0" style="text-anchor: middle;">December</text></g>
		<path class="domain" d="M0,0V0H520V0"></path></g>
			<g class="axis"><g class="tick" transform="translate(0,420)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">0</text></g>
			<g class="tick" transform="translate(0,378)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">5</text></g>
			<g class="tick" transform="translate(0,336)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">10</text></g>
			<g class="tick" transform="translate(0,294)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">15</text></g>
			<g class="tick" transform="translate(0,252)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">20</text></g>
			<g class="tick" transform="translate(0,210)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">25</text></g>
			<g class="tick" transform="translate(0,168)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">30</text></g>
			<g class="tick" transform="translate(0,126.00000000000001)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">35</text></g>
			<g class="tick" transform="translate(0,83.99999999999999)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">40</text></g>
			<g class="tick" transform="translate(0,41.99999999999999)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">45</text></g>
			<g class="tick" transform="translate(0,0)" style="opacity: 1;"><line x2="-6" y2="0"></line>
				<text dy=".32em" x="-14" y="0" style="text-anchor: end;">50</text></g><path class="domain" d="M-6,0H0V420H-6"></path></g>
			<g class="grid"><g class="tick" transform="translate(0,420)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,399)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,378)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,357)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,336)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,315)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,294)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,273)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,252)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,231.00000000000003)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,210)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,188.99999999999997)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,168)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,147)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,126.00000000000001)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,105)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,83.99999999999999)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,63.00000000000001)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,41.99999999999999)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,21.000000000000018)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
			<g class="tick" transform="translate(0,0)" style="opacity: 1;"><line x2="868" y2="0"></line>
				<text dy=".32em" x="-3" y="0" style="text-anchor: end;"></text></g>
				<path class="domain" d="M0,0H0V420H0"></path></g>
			
			<rect class="bar" x="0" y="323" width="15" height="97"></rect>
			<rect class="bar" x="74" y="301" width="15" height="120"></rect>
			<rect class="bar" x="148" y="266" width="15" height="155"></rect>
			<rect class="bar" x="223" y="226" width="15" height="195"></rect>
			<rect class="bar" x="297" y="191" width="15" height="230"></rect>
			<rect class="bar" x="371" y="168" width="15" height="253"></rect>
			<rect class="bar" x="445" y="150" width="15" height="271"></rect>
			<rect class="bar" x="519" y="160" width="15" height="261"></rect>
			<rect class="bar" x="609" y="180" width="15" height="241"></rect>
			<rect class="bar" x="683" y="226" width="15" height="195"></rect>
			<rect class="bar" x="757" y="266" width="15" height="155"></rect>
			<rect class="bar" x="831" y="318" width="15" height="102"></rect>
				<text x="0" y="323" dx="0.5em" dy="1.50em" text-anchor="left">11</text>
				<text x="74" y="301" dx="0.5em" dy="1.50em" text-anchor="left">14</text>
				<text x="148" y="266" dx="0.5em" dy="1.50em" text-anchor="left">18</text>
				<text x="223" y="226" dx="0.5em" dy="1.50em" text-anchor="left">23</text>
				<text x="297" y="191" dx="0.5em" dy="1.50em" text-anchor="left">27</text>
				<text x="371" y="168" dx="0.5em" dy="1.50em" text-anchor="left">30</text>
				<text x="445" y="150" dx="0.5em" dy="1.50em" text-anchor="left">32</text>
				<text x="519" y="160" dx="0.5em" dy="1.50em" text-anchor="left">31</text>
				<text x="609" y="180" dx="0.5em" dy="1.50em" text-anchor="left">28</text>
				<text x="683" y="226" dx="0.5em" dy="1.50em" text-anchor="left">23</text>
				<text x="757" y="266" dx="0.5em" dy="1.50em" text-anchor="left">18</text>
				<text x="831" y="318" dx="0.5em" dy="1.50em" text-anchor="left">12</text>
				<text x="500" y="-20" text-anchor="middle" style="font-size: 20px;">Average Daily High(°C) by Month - Atlanta, Georgia</text>
				</g>
			</svg>
		</div>
	</body>
</html>
