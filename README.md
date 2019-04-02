# currency_convertor
<html>
  <head>
  <link href="https://fonts.googleapis.com/css?family=ZCOOL+XiaoWei" rel="stylesheet">
   <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/js/bootstrap.min.js"></script>
</head>
<body>


  <script>
    function convert(){
			var from =document.getElementById("from").value;
			var to = document.getElementById("to").value;
			var xmlhttp= new XMLHttpRequest();
			var url="https://free.currencyconverterapi.com/api/v6/convert?q="+from+"_"+to+"&compact=ultra&apiKey=b165e86d77813b82cc13";
			xmlhttp.open("GET", url, true);//async
			xmlhttp.send();
			xmlhttp.onreadystatechange=function(){
				if(this.readyState === 4 && this.status === 200 )
				{	var result=this.responseText;
					console.log(result);
					var jsResult=JSON.parse(result);
          var q = from+"_"+to;
          console.log(q);
          console.log(jsResult[q]);
          var amount = jsResult[q] * document.getElementById('from_VAL').value;
          console.log(amount);
					document.getElementById("to_VAL").value= amount;
				}
      }
	  } 
	</script>
  <style>

input[type=text], select {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 2px dotted green;
    border-radius: 4px;
    box-sizing: border-box;
	background-color: #ecf9ec;
font-family: 'Comfortaa', cursive;
}
input[type=text]:hover {
    border: 3px solid green;
}

h1 {
font-family: 'ZCOOL XiaoWei', serif;}

button {
font-family: 'ZCOOL XiaoWei', serif;}
div {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
}
@media screen and (max-width: 600px) {
    .col-25, .col-75, input[type=submit] {
        width: 100%;
        margin-top: 0;
    }
}
body {

  background-image: url("NN-LOGO.png");
  background-position: 50% 50%;
  background-repeat: repeat;
   background-color: rgba(255,255,255,0.6);
  background-blend-mode: lighten;
}
form {
	padding: 130px 150px;
}

  </style>
</head>
<body>
  <div>
   <center> <h1>Currency Converter</h1></center>
  </div>
  <div class="container">

  </div>
  <div class="container">
<input type="text" value="0" name="from_VAL" id="from_VAL" placeholder="Enter amount" />
     
    <br>
    <div class="medium-3 columns">
      <select id="from" class="postfix">
        <option value="AUD" >AUD</option>
        <option value="AZN" >AZN</option>
        <option value="BHD" >BHD</option>
        <option value="CAD" >CAD</option>
        <option value="CHF" >CHF</option>
        <option value="EUR" >EUR</option>
        <option value="GBP" >GBP</option>
        <option value="INR" >INR</option>
        <option value="JOD" >JOD</option>
        <option value="KWD" >KWD</option>
        <option value="KYD" >KYD</option>
        <option value="OMR" >OMR</option>
        <option value="USD" selected>USD</option>
        <option value="UYU" >UYU</option>
      </select>
    </div>
   <button type="button" name="button" class="btn btn-success" onclick="convert()"> Convert Currency!! </button>
     <div class="medium-3 columns">
       <select id="to" class="postfix">
         <option value="AUD" >AUD</option>
         <option value="AZN" >AZN</option>
         <option value="BHD" >BHD</option>
         <option value="CAD" >CAD</option>
         <option value="CHF" >CHF</option>
         <option value="EUR" >EUR</option>
         <option value="GBP" >GBP</option>
         <option value="INR" selected>INR</option>
         <option value="JOD" >JOD</option>
         <option value="KWD" >KWD</option>
         <option value="KYD" >KYD</option>
         <option value="OMR" >OMR</option>
         <option value="USD">USD</option>
         <option value="UYU" >UYU</option>
       </select>
    </div>
    <br>
    <div class="medium-3 columns">
      <input type="text" id="to_VAL" readonly placeholder="get value" disabled style="background-color: #eee; font-weight: bold;" value=0 />
    </div>
  </div>
</body>
</html>
