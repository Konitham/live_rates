# live_rates

//html5
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>soccer score</title>
</head>
<body>
   <h1 id="score_value">---</h1>
   <script src="app.js"></script>

</body>
</html>

// js

let ws = new WebSocket('wss://stream.binance.com:9443/ws/etheur@trade')
let stockPriceElement = document.getElementById("score_value")
let lastPrice = null;
ws.onmessage = (Event) => {
    let stockObject = JSON.parse(Event.data);
    let price = parseFloat(stockObject.p);
    stockPriceElement.innerText = price;
    stockPriceElement.style.color = !lastPrice === price ? "black" : price > lastPrice ?  "green" : "red";
    lastPrice = price;
}
