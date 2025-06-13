<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Zamfara Commodity Price Checker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f4f8;
      padding: 20px;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      color: #2c3e50;
    }
    select, table {
      width: 100%;
      margin-top: 20px;
    }
    table {
      border-collapse: collapse;
    }
    th, td {
      padding: 12px;
      border: 1px solid #ccc;
      text-align: left;
    }
    th {
      background-color: #2980b9;
      color: white;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Zamfara Price Checker</h1>
    <label for="localGov">Select Local Government:</label>
    <select id="localGov" onchange="showPrices()">
      <option value="">-- Select Local Government --</option>
      <option value="Gusau">Gusau</option>
      <option value="Kaura Namoda">Kaura Namoda</option>
      <option value="Talata Mafara">Talata Mafara</option>
    </select><table id="priceTable" style="display:none">
  <thead>
    <tr>
      <th>Commodity</th>
      <th>Price (₦)</th>
    </tr>
  </thead>
  <tbody id="priceBody"></tbody>
</table>

  </div>  <script>
    const prices = {
      "Gusau": {
        "Rice (50kg)": 40000,
        "Beans (50kg)": 38000,
        "Maize (50kg)": 30000
      },
      "Kaura Namoda": {
        "Rice (50kg)": 42000,
        "Beans (50kg)": 37000,
        "Maize (50kg)": 31000
      },
      "Talata Mafara": {
        "Rice (50kg)": 41000,
        "Beans (50kg)": 39000,
        "Maize (50kg)": 30500
      }
    };

    function showPrices() {
      const lg = document.getElementById("localGov").value;
      const table = document.getElementById("priceTable");
      const tbody = document.getElementById("priceBody");

      tbody.innerHTML = ""; // Clear existing

      if (prices[lg]) {
        table.style.display = "table";
        const commodities = prices[lg];
        for (const [commodity, price] of Object.entries(commodities)) {
          const row = `<tr><td>${commodity}</td><td>₦${price.toLocaleString()}</td></tr>`;
          tbody.innerHTML += row;
        }
      } else {
        table.style.display = "none";
      }
    }
  </script></body>
</html>
