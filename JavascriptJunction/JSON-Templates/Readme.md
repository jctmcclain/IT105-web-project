# JSON Templates

## Inline 

## Remote
``` JAVASCRIPT
<div id="recordset"></div>
<hr>
</div>
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
