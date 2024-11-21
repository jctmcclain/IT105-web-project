# JSON Templates

## Inline 
```JAVASCRIPT
<script>
data = '[';
data += '{"attribone":"Item One 1","attribtwo":"Item Two 1","attribthree":"Item Three 1"},'
data += '{"attribone":"Item One 2","attribtwo":"Item Two 2","attribthree":"Item Three 2"}'
data += ']';

var mydata = JSON.parse(data);
rs = '<div class="row">';
rs += '   <div class="col-md-4"><b>Attribute One</b></div>';
rs += '   <div class="col-md-4"><b>Attribute Two</b></div>';
rs += '   <div class="col-md-4"><b>Attribute Three</b></div>';
rs += '</div>';
for(i=0;i<mydata.length;i++) {
	rs += '<div class="row">';
	rs += '   <div class="col-md-4">' + mydata[i].attribone + '</div>';
	rs += '   <div class="col-md-4">' + mydata[i].attribtwo + '</div>';
	rs += '   <div class="col-md-4">' + mydata[i].attribthree + '</div>';
	rs += '</div>';
} 
document.getElementById("recordset").innerHTML = rs;
</script>


```

## Remote
``` JAVASCRIPT
<div id="recordset"></div>
<hr>
<script>
function fetchJSONData() {
	fetch("./mycool.json").then((res) => {
		if (!res.ok) {
			throw new Error(`HTTP error! Status: ${res.status}`);
        }
        return res.json();
	})
    .then((data) => {
		rs =  '<div class="row">';
		rs += '   <div class="col-md-4"><h4>Attribute One</h4></div>';
		rs += '   <div class="col-md-4"><h4>Attribute Two</h4></div>';
		rs += '   <div class="col-md-4"><h4>Attribute Three</h4></div>';
		rs += '</div>';
		for(i=0;i<data.length;i++) {
			rs += '<div class="row">';
			rs += '   <div class="col-md-4">' + data[i].attribone + '</div>';
			rs += '   <div class="col-md-4">' + data[i].attribtwo + '</div>';
			rs += '   <div class="col-md-4">' + data[i].attribthee + '</div>';
			rs += '</div>';
		} 
		document.getElementById("recordset").innerHTML = rs;
	})
	.catch((error) =>
		console.error("Unable to fetch data:", error));
}
fetchJSONData();

</script>
```
