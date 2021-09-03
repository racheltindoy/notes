- ajax uses XHR API to handle request from the server
- needs to be in a server to run


# scripts for backwards compatibility

```
var request;
if (window.XMLHttpRequest) {
  request = new XMLHttpRequest();
} else {
  request = new ActiveXObject("Microsoft.XMLHttp")
}
```

# assigning result to an html element
```
var request;
if(window.XMLHttpRequest) {
    request = new XMLHttpRequest();
} else {
    request = new ActiveXObject("Microsoft.XMLHTTP");
}
request.open('GET', 'data.txt', false)
request.onreadystatechange = function() {
    if((request.readyState === 4) && (request.status === 200)) {
       var modify = document.getElementById('update');
       modify.innerHTML = request.responseText;
     }
}
request.send();
```

# responseXML to parse XML format

```
var request;
if(window.XMLHttpRequest) {
    request = new XMLHttpRequest();
} else {
    request = new ActiveXObject("Microsoft.XMLHTTP");
}
request.open('GET', 'data.xml', false)
request.onreadystatechange = function() {
    if((request.readyState === 4) && (request.status === 200)) {
        console.log(request.responseXML.getElementsByTagName('name')[0].firstChild.nodeValue);

        var items = request.responseXML.getElementsByTagName('name');
        var output;

        output = "<ul>";
        for(i = 0; i < items.length; i++) {
            output += "<li>";
            output +=  items[i].firstChild.nodeValue;
            output += "</li>";
        }
        document.getElementById('update').innerHTML = output;
     }
}
request.send();
```

# JSON.parse(request.responseText) to parse JSON files

```
var request;
if(window.XMLHttpRequest) {
    request = new XMLHttpRequest();
} else {
    request = new ActiveXObject("Microsoft.XMLHTTP");
}
request.open('GET', 'data.json', false)
request.onreadystatechange = function() {
    if((request.readyState === 4) && (request.status === 200)) {
        console.log(JSON.parse(request.responseText));

        var items = JSON.parse(request.responseText);
        var output = "<ul>";
        for(var key in items) {
            output += "<li>";
            output +=  items[key].name;
            output += "</li>";
        }
        document.getElementById('update').innerHTML = output;
     }
}
request.send();
```
