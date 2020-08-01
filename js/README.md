# JavaScript Best Practices and Snippets
This section contains documentations, best practices, design patterns and hacks with basic code snippets for JS.


### Code Snippets

How to **dynamic POST form data into new page**. 
here is the [link to the code](./dynamic-post-form.js) snippet.
``` js
var params = {
    username: "username",
    password: "password"
};

var form = document.createElement("form");
form.setAttribute("method", "post");
form.setAttribute("action", "https://url:port/url");
//creating dynamic hidden inputs for submissions
for (var key in params) {
    var hiddenField = document.createElement("input");
    hiddenField.setAttribute("type", "hidden");
    hiddenField.setAttribute("name", key);
    hiddenField.setAttribute("value", params[key]);
    form.appendChild(hiddenField);
}
var url = 'data:text/html;charset=utf8,';
url += encodeURIComponent(form.outerHTML);
url += encodeURIComponent('<script>document.forms[0].submit();</script>');

// A general method
window.open(url);
// or in chrome extensions
chrome.tabs.create({
    url: url
});
```
