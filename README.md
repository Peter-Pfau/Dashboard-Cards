# Dashboard-Cards
Building dashboards with containers cards and APIs

## Main Grid Container 3 Columns
```css
.grid-container{
	display: grid;
	grid-template-columns: 1fr 10fr 1fr;
}
.grid-item-LeftColumn{
	background-color: white;
}
.grid-item-MiddleColumn{
	background-color: white;
}
.grid-item-RightColumn{
	background-color: white;
}

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

### Menu.html

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
## Cards
CSS

```css
.flex-container {
display: flex;
flex-direction: row;
flex-wrap: wrap;
justify-content: center;
background-color: rgb(248, 249, 251);
border-radius: 25px;
}

.flex-container > div {
background-color: white;
width: 400px;
margin: 10px;
text-align: center;
line-height: 75px;
font-size: 15px;
}
.card-wrapper{
    display: grid;
    grid-template-columns: 100px 250px;
    grid-template-rows: 55px 75px 50px;
    grid-template-areas:
        "side header"
        "side main"
        "side footer";
        margin: 5px;
    border: 0;
    border-radius: 10px;
    padding: 20px 0px 10px 0px;
    box-shadow: 0 5px 5px rgb(0 0 0 / 49%);
    font-size: large;
    width: 400px;   
}
.bgCard1{
    background-image: url('./Images/Forest.jpg');
    background-size: cover;
    opacity: 0.5;
    
}
.bgCard2{
    background-image: url('./Images/Schema.jpg');
    background-size: cover;
    opacity: 0.5;
}
.bgCard3{
    background-image: url('./Images/Tombstone.jpg');
    background-size: cover;
    opacity: 0.5;
}

.header{
    display: grid;
    /* background: whitesmoke; */
    grid-area: header;
    text-align: center;
    font-weight: 600;
    padding: 5px;
}
.side{
    display: grid;
    /* background: yellow; */
    grid-area: side;
    border-radius: 10px 0px 0px 10px;
    /* box-shadow: 0 5px 5px rgb(0 0 0 / 49%); */
    
}
.main{
    display: grid;
    /* background: greenyellow; */
    grid-area: main;
    text-align: center;
    font-size: 30px;
    font-weight: 400;
    border-radius: 0px 0px 5px 0px;
    /* box-shadow: 0 5px 5px rgb(0 0 0 / 49%); */
}
.main-Small{
    display: grid;
    /* background: greenyellow; */
    grid-area: main;
    text-align: center;
    font-size: 23px;
    font-weight: 600;
    border-radius: 0px 0px 5px 0px;
    /* box-shadow: 0 5px 5px rgb(0 0 0 / 49%); */
}
.foot{
    display: flex;
    padding-left: 5px;
    padding-right: 5px;
    padding-top: 5px;
    justify-content: flex-end;
}
.foot > div{
    padding-right: 10px;
}
```
HTML
```css
        <div class="flex-container">
            <div class="card-wrapper">
                <header class="header">Forest Mode</header>
                <section class="side bgCard1"></section>
                <main id="ForestMode" class="main-Small"></main>
                <foot class="foot">
                    <div id="ForestModeValue"></div>
                    <div id="ForestDate"></div>
                </foot>
            </div>
            <div class="card-wrapper card-2">
                <header class="header">Schema Version</header>
                <section class="side bgCard2"></section>
                <main id="SchemaVersion" class="main-Small"></main>
                <foot class="foot">
                    <div id="SchemaVersionValue"></div>
                    <div id="SchemaVersionDate"></div>
                </foot>
            </div>
            <div class="card-wrapper card-3">
                <header class="header">Tombstone Lifetime</header>
                <section class="side bgCard3"></section>
                <main id="TombstoneLifetime" class="main"></main>
                <foot class="foot">
                    <div id="TombstoneLifetimeDate"></div>
                </foot>
            </div>
	</div>

```
