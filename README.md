<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
<style>
.vertical-menu {
    width: 200px;
}

.vertical-menu a {
    background-color: #eee;
    color: black;
    display: block;
    padding: 12px;
    text-decoration: none;
}

.vertical-menu a:hover {
    background-color: #ccc;
}

.vertical-menu a.active {
    background-color: #4CAF50;
    color: white;
}
</style>
<script>
        function loadJSON(file, callback) {   

    var xobj = new XMLHttpRequest();
    xobj.overrideMimeType("application/json");
    xobj.open('GET', file, true); // Replace 'my_data' with the path to your file
    xobj.onreadystatechange = function () {
          if (xobj.readyState == 4 && xobj.status == "200") {
            // Required use of an anonymous callback as .open will NOT return a value but simply returns undefined in asynchronous mode
            callback(xobj.responseText);
          }
    };
    xobj.send(null);  
 }
 

function init() {
    
    loadJSON("http://cat-store-api.frostdigital.se/api", function(response) {
  
        var actual_JSON = JSON.parse(response);
		console.log("init");
        console.log(actual_JSON.products[0].stock);
    });
    
    
}
init();
        var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        var myObj = JSON.parse(this.responseText);
        document.getElementById("demo").innerHTML = myObj.products[0].price[0];
    }
};
xmlhttp.open("GET", "data.txt", true);
xmlhttp.send();
    </script>
    <script language="JavaScript">
 
        function show(shown, hidden) {
        document.getElementById(shown).style.display='block';
        document.getElementById(hidden).style.display='none';
        return false;
        }
       
        function AddtoCart() {
                console.log( 'hi');
                var x=document.getElementById('Items');
                var new_row = x.rows[1].cloneNode(true);
                var len = x.rows.length;
                new_row.cells[0].innerHTML = len;
   
                var inp1 = new_row.cells[1].getElementsByTagName('input')[0];
                inp1.id += len;
                inp1.value = '';
                var inp2 = new_row.cells[2].getElementsByTagName('input')[0];
                inp2.id += len;
                inp2.value = '';
                x.appendChild( new_row );
        }
 
</script>
</head>
<body style="background-color: whitesmoke">
    <div id="Main">

<h1 align="center">Welcome to Catstore</h1>
<h3 align="center">Product Menu</h3>
    <p align="center"> View Cart    <a href="#" onclick="return show('Cart','Main');"> <img src="cart.png" height=50px width=45px> </img> </a> </p>
<p id="demo"></p>


    
    <table id="Items" align="center" border="1" bgcolor="white">
               
        <tr>
        <td>Product Name</td>
        <td>Price</td>
        <td></td>
        </tr>
                <tr>
                        <td>Kattborste</td>
                        <td>199 SEK</td>
                        <td> <input type="image" src="submit-button.jpg" name="Cart" height="100px" width="100px" onclick="AddtoCart()"> </td>
                </tr>
               
                <tr>
                        <td>Royal Canin Sterilised 37 10 kg (kattmat)</td>
                        <td>250 SEK</td>
                        <td> <input type="image" src="submit-button.jpg" name="Cart" height="100px" width="100px" onclick="AddtoCart()"> </td>
                </tr>
               
                <tr>
                        <td>Puppy Angel tröja</td>
                        <td>250 SEK</td>
                        <td> <input type="image" src="submit-button.jpg" name="Cart" height="100px" width="100px" onclick="AddtoCart()"> </td>
                </tr>
       
        <tr>
                        <td>Hårband</td>
                        <td>20 SEK</td>
                        <td> <input type="image" src="submit-button.jpg" name="Cart" height="100px" width="100px" onclick="AddtoCart()"> </td>
                </tr>
       
    </table> 
    </div>

    <!--<div class="vertical-menu">
  <a href="#" class="active">Home</a>
  <a href="http://cat-store-api.frostdigital.se/api">Kattborste</a>
  <a href="http://cat-store-api.frostdigital.se/api">Royal Canin Sterilised 37 10 kg (kattmat)</a>
  <a href="http://cat-store-api.frostdigital.se/api">Puppy Angel Troja</a>
  <a href="http://cat-store-api.frostdigital.se/api">Hårband</a> -->
 
<div id="Cart" style="display:none">
       
        <h1 align="center">Thanks for shopping</h1>
   

       
   <p align="center"> <a href="#" onclick="return show('Main','Cart');">Return</a> </p>
 
  </div>
   
</body>
</html>
