# Dashboard-Cards
Building dashboards with containers cards and APIs

## Main Grid Container 3 Columns

```css
    <div class="grid-container">  
        <div class="grid-item grid-item-LeftColumn"></div>
        <div class="grid-item grid-item-MiddleColumn"><!-- Middle column --></div>
        <div class="grid-item grid-item-RightColumn"></div>
    </div>
```
## Nav

```css
    <div w3-include-html="assets/nav/menu.html"></div>
```

## Menu.html

```css
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width", initial-scale="1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <link rel="stylesheet" href="../css/stylemenu.css">
    <title>VA Authentication Services</title>
</head>
<body >
    <div class="menu__bar">
        <div><h1 class="logo">Co.<span> Department</span></h1></div>
        <UL>
            <li><a href="#">Home</a></li>
            <li><a href="#">Menu_Item_1<i class="fas fa-caret-down"></i></a>
            <div class="dropdown__menu">
                <UL>
                    <li><a href="#">Sub_Menu_Item_1<i class="fas fa-caret-right"></i></a>
                        <div class="dropdown__menu-1"> 
                            <ul>
                                <li><a href="#">Sub2_Menu1</a></li>
                                <li><a href="#">Sub2_Menu2</a></li>          
                            </ul>
                        </div>
                    </li>
                </UL>
           </div>
           </li>
        </UL>
    </div>
</body>
</html>
```

## Footer

```css
    <footer>
        <div w3-include-html="assets/nav/footer.html"></div>
    </footer>

    <script src="assets/js/include.js"></script>

```
## Using JavaScript for HTML Includes
One of the simplest ways to include HTML files is by using a custom attribute and JavaScript. This method involves creating a div element with a custom attribute, such as w3-include-html, and then using JavaScript to load the content of the specified HTML file into this div.
```js
function includeHTML() {
  var z, i, elmnt, file, xhttp;
  /* Loop through a collection of all HTML elements: */
  z = document.getElementsByTagName("*");
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    /*search for elements with a certain atrribute:*/
    file = elmnt.getAttribute("w3-include-html");
    if (file) {
      /* Make an HTTP request using the attribute value as the file name: */
      xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function() {
        if (this.readyState == 4) {
          if (this.status == 200) {elmnt.innerHTML = this.responseText;}
          if (this.status == 404) {elmnt.innerHTML = "Page not found.";}
          /* Remove the attribute, and call this function once more: */
          elmnt.removeAttribute("w3-include-html");
          includeHTML();
        }
      }
      xhttp.open("GET", file, true);
      xhttp.send();
      /* Exit the function: */
      return;
    }
  }
}
```
