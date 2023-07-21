
<html>
<head>
  <title>Benny's Original</title>
    <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 250vh;
      text-align: center;
    }
	.total-box {
		display: flex;
		justify-content: center; /* Center horizontally */
		align-items: center; /* Center vertically */
		margin-top: 20px;
	}}
	
	 .calculate-button {
      width: 150px; /* Adjust the desired width */
      height: 30px; /* Adjust the desired height */
    }
	
	.submit-button {
      width: 150px; /* Adjust the desired width */
      height: 40px; /* Adjust the desired height */
    }
	
	.reset-button {
      width: 150px; /* Adjust the desired width */
      height: 30px; /* Adjust the desired height */
    }
    
    h1 {
      margin-bottom: 20px;
    }
    
    h2 {
      margin-top: 20px;
    }
	
	h3 {
      border: 1px solid black; /* Adjust the border style as needed */
      padding: 5px; /* Add padding to create space around the heading */
    }
    
    .menu-items {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 10px;
    }
    
    .menu-items div {
      display: flex;
      align-items: center;
    }
    
    .total-box {
      display: flex;
      justify-content: flex-end;
      align-self: flex-end;
      margin-top: 20px;
    }
    
    .button-container {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
	
	.menu-items div img {
      width: 50px; /* Adjust the desired width */
      height: 50px; /* Adjust the desired height */
      margin-left: 10px; /* Add margin as per your preference */
    }
	
    {
    button {
      margin-top: 20px;
	}}}}}}
  </style>
  <script>
    function calculateTotal() {
    var total = 0;
    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');

    checkboxes.forEach(function(checkbox) {
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var price = parseFloat(checkbox.value);

      if (checkbox.value === '-25%') {
        var itemPrice = total * 0.25;
        total -= itemPrice;
      } else if (checkbox.value === '-30%') {
        var itemPrice = total * 0.3;
        total -= itemPrice;
      } else if (checkbox.value === '-50%') {
        var itemPrice = total * 0.5;
        total -= itemPrice;
      } else {
        total += price * quantity;
      }
    });

    var totalElement = document.getElementById('total');
    totalElement.textContent = total.toFixed(2);

    var discountTotalElement = document.getElementById('discount-total');
    var discount = total * 0.05;
    discountTotalElement.textContent = discount.toFixed(2);
  }


    
    function submitOrder() {
    var name = document.getElementById('name').value;

    // Check if the name field is empty
    if (name.trim() === '') {
      alert('Who are you?');
      return;
    }

    var total = parseFloat(document.getElementById('total').textContent);
    var discordWebhookURL = 'https://discord.com/api/webhooks/1118343660623380580/Uhs34Lq96Q3zW5AoKvkOXKLxdqRZJiu1U-B85KW_dR8Sq5nftRKhQNr9BjrgFa75Nbza'; // Replace with your Discord webhook URL

    var xhr = new XMLHttpRequest();
    xhr.open('POST', discordWebhookURL, true);
    xhr.setRequestHeader('Content-Type', 'application/json');

    var message = {
      content: 'Upgrade Receipt!',
      embeds: [{
        title: 'Order Details',
        fields: [
          {
            name: 'Name',
            value: name,
            inline: true
          },
          {
            name: 'Total',
            value: '$' + total.toFixed(2),
            inline: true
          }
        ]
      }]
    };

    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');
    checkboxes.forEach(function (checkbox) {
      var itemLabel = checkbox.nextElementSibling.textContent;
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var itemTotal = parseFloat(checkbox.value) * quantity;
      message.embeds[0].fields.push({
        name: itemLabel,
        value: 'Quantity: ' + quantity + ', Total: $' + itemTotal.toFixed(2),
        inline: false
      });
    });

    xhr.send(JSON.stringify(message));
  }

  function resetCalculator() {
    var checkboxes = document.querySelectorAll('input[type="checkbox"]');
    var quantityInputs = document.querySelectorAll('input[type="number"]');

    checkboxes.forEach(function (checkbox) {
      checkbox.checked = false;
    });

    quantityInputs.forEach(function (quantityInput) {
      quantityInput.value = 1;
    });

    document.getElementById('total').textContent = '0.00';
  }
  </script>
</head>
<body>
<body style="background-color:White;">
<body style="text-color:Red;">
	<img src="BackGround1.png" alt="Company Logo!">
  <h1>Performance Upgrade Sheet</h1>
  
  
  
  <h3> ENGINE </h3>
  
  <div>
    <input type="checkbox" id="ColinChoice" value="1000">
    <label for="ColinChoice">Engine Level 1</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="JudysChoice" value="3000">
    <label for="JudysChoice">Engine Level 2</label>
    <input type="number" value="1" min="1">
  </div>

<div>
    <input type="checkbox" id="Velmachoice" value="8000">
    <label for="Velmachoice">Engine Level 3</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> SUSPENSION </h3>
  
  <div>
    <input type="checkbox" id="Velmachoice" value="100">
    <label for="Velmachoice">Suspension Level 1</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Velmachoice" value="3000">
    <label for="Velmachoice">Suspension Level 2</label>
    <input type="number" value="1" min="1">
  </div>

    <div>
    <input type="checkbox" id="Velmachoice" value="5000">
    <label for="Velmachoice">Suspension Level 3</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> TRANSMISSION </h3>
  
  <div>
    <input type="checkbox" id="Salad" value="1000">
    <label for="Salad">Transmission Level 1</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FruitExplosion" value="4000">
    <label for="FruitExplosion">Transmission Level 2</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="TurkeySammie" value="7000">
    <label for="TurkeySammie">Transmission Level 3</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> BRAKES </h3>
  
   <div>
    <input type="checkbox" id="BeefSammie" value="1000">
    <label for="BeefSammie">Brakes Level 1</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="BLTSammie" value="5000">
    <label for="BLTSammie">Brakes Level 2</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="8000">
    <label for="choccypanckaes">Brakes Level 3</label>
    <input type="number" value="1" min="1">
  </div>

    <h3> TURBO </h3>
  
  <div>
    <input type="checkbox" id="cat30" value="12000">
    <label for="cat30">D - A Class Vehicles</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="cat50" value="15000">
    <label for="cat40">S Class Vehicles</label>
    <input type="number" value="1" min="1">
  </div>

    <h3> REPAIR </h3>
  
  <div>
    <input type="checkbox" id="cat30" value="1400">
    <label for="cat30">D - A Class Vehicles</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="cat50" value="2400">
    <label for="cat40">S Class Vehicles</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 100px;"></div>

<div>
    <label for="name">Employee's Name:</label>
    <input type="text" id="name">
  </div>

<div style="margin-bottom: 60px;"></div>

 
<div class="total-box">
  <span>Total: $</span>
  <span id="total">0.00</span>
</div>

 
  
  
  <div style="margin-bottom: 10px;"></div>
  

  
  <div style="margin-bottom: 30px;"></div>

  <button class="calculate-button" onclick="calculateTotal()">Calculate Total</button>
  <button class="submit-button" onclick="submitOrder()">Submit Order</button>
  <button class="reset-button" onclick="resetCalculator()">Reset</button>
  
  
  <div style="margin-bottom: 100px;"></div>
