[Wataha.html](https://github.com/user-attachments/files/24416863/Wataha.html)
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Trade Your Passion for Glory - Wataha Team</title>
  <style>
    body {
      background: linear-gradient(135deg, #0a0a0a, #0f1b2d);
      color: white;
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      text-align: center;
    }
    header {
      padding: 30px;
      background: #101820;
      color: #9ec9ff;
      font-size: 26px;
      font-weight: bold;
      letter-spacing: 1px;
    }
    section {
      padding: 40px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 30px;
    }
    .product {
      background: rgba(15, 25, 40, 0.9);
      border: 2px solid #1f3b6b;
      border-radius: 20px;
      width: 300px;
      padding: 20px;
      box-shadow: 0 0 20px rgba(0, 120, 255, 0.3);
      transition: 0.3s;
    }
    .product:hover {
      box-shadow: 0 0 25px rgba(0, 120, 255, 0.6);
      transform: translateY(-5px);
    }
    h2 {
      color: #b0d8ff;
    }
    .price {
      font-size: 20px;
      color: #00bfff;
      margin: 15px 0;
    }
    button {
      background-color: #0070ba;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 10px;
      cursor: pointer;
      font-size: 16px;
      transition: 0.3s;
    }
    button:hover {
      background-color: #009cde;
    }
    footer {
      margin-top: 50px;
      padding: 20px;
      background: #0f1a25;
      color: #7fa5cc;
    }
  </style>
</head>
<body>
  <header>🐺 Wataha Team - Trade Your Passion for Glory</header>

  <section>
    <div class="product">
      <h2>🎯 Pakiet Trade Your Passion for Glory</h2>
      <p>15+ video-lekcji, dropmapa, plan treningowy (PRO), efekty: lepszy aim, rotacje, mniej błędów.</p>
      <p class="price">💰 Cena: 30 zł (Standard) / 40 zł (PRO)</p>
      <button onclick="setPrice(30)">Kup Standard</button>
      <button onclick="setPrice(40)">Kup PRO</button>
    </div>

    <div class="product">
      <h2>🗺️ Dropmap - Fortnite</h2>
      <p>Najlepsze spoty, rotacje i trasy, które zwiększą Twoje wyniki.</p>
      <p class="price">💰 Cena: 10 zł</p>
      <button onclick="setPrice(10)">Kup Dropmap</button>
    </div>
  </section>

  <div id="paypal-button-container" style="margin:40px auto; width:300px;"></div>

  <footer>
    🔒 100% Bezpieczne – bez cheatów, czysty skill<br />
    📞 Blik: 668 570 678 | 📧 PayPal: ramcraft2000@gmail.com
  </footer>

  <script src="https://www.paypal.com/sdk/js?client-id=AVKRH6dVvFD3AL9BctiSyAZL_Wk0mZjDsUGx32U11Krie72YzaZMe7Z0oInt17hl3VGL5xMzVAJxUc-C&currency=PLN"></script>

  <script>
    let selectedPrice = 0;

    function setPrice(price) {
      selectedPrice = price;
      alert("Wybrano produkt za " + price + " zł. Możesz zapłacić PayPal poniżej 👇");
    }

    paypal.Buttons({
      style: {
        layout: 'vertical',
        color: 'blue',
        shape: 'rect',
        label: 'paypal'
      },
      createOrder: function(data, actions) {
        if (selectedPrice <= 0) {
          alert("Najpierw wybierz produkt!");
          return;
        }
        return actions.order.create({
          purchase_units: [{
            amount: {
              value: selectedPrice.toFixed(2)
            },
            description: "Zakup na stronie Wataha Team - Trade Your Passion for Glory"
          }]
        });
      },
      onApprove: function(data, actions) {
        return actions.order.capture().then(function(details) {
          alert('✅ Dziękujemy, ' + details.payer.name.given_name + '! Płatność zakończona sukcesem.');
        });
      },
      onError: function(err) {
        console.error(err);
        alert("❌ Wystąpił błąd podczas płatności PayPal.");
      }
    }).render('#paypal-button-container');
  </script>
</body>
</html>
