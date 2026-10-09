
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tenant Maintenance & Payment Portal</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f1f5f9;
      color: #1e293b;
    }
    header {
      background: #12345a;
      color: white;
      padding: 24px 16px;
      text-align: center;
    }
    main {
      max-width: 600px;
      margin: 20px auto;
      padding: 16px;
    }
    .card {
      background: white;
      padding: 20px;
      margin-bottom: 16px;
      border-radius: 12px;
      box-shadow: 0 2px 8px #00000012;
    }
    h2 { color: #12345a; }
    label {
      display: block;
      margin-top: 12px;
    }
    input, select, button {
      box-sizing: border-box;
      width: 100%;
      padding: 12px;
      margin-top: 6px;
      border-radius: 6px;
      font-size: 16px;
    }
    input, select { border: 1px solid #cbd5e1; }
    button {
      background: #12345a;
      color: white;
      border: none;
      margin-top: 16px;
    }
    .notice { color: #9a3412; font-size: 14px; }
  </style>
</head>
<body>
  <header>
    <h1>Tenant Portal</h1>
    <p>Maintenance, Payments & Receipts</p>
  </header>

  <main>
    <section class="card">
      <h2>Welcome</h2>
      <p>Manage your apartment maintenance fees, fuel contributions and repair payments in one place.</p>
      <p class="notice">Demo website: payments and accounts are not connected yet.</p>
    </section>

    <section class="card">
      <h2>Payment Record</h2>
      <label for="tenant">Tenant name</label>
      <input id="tenant" placeholder="Enter tenant name">

      <label for="type">Payment type</label>
      <select id="type">
        <option>Maintenance fee</option>
        <option>Generator fuel</option>
        <option>Repairs</option>
      </select>

      <label for="amount">Amount (GH₵)</label>
      <input id="amount" type="number" min="0.01" step="0.01" placeholder="Enter amount">

      <label for="method">Payment method</label>
      <select id="method">
        <option>Manual payment</option>
        <option>Online payment (not connected)</option>
      </select>

      <button onclick="recordPayment()">Preview Payment Record</button>
      <div id="result" aria-live="polite"></div>
    </section>

    <section class="card">
      <h2>Portal Features</h2>
      <ul>
        <li>Maintenance fee records</li>
        <li>Generator fuel contributions</li>
        <li>Repair payment records</li>
        <li>Payment receipts</li>
        <li>Outstanding balance tracking</li>
        <li>Tenant and supervisor access (to be built)</li>
      </ul>
    </section>
  </main>

  <script>
    function recordPayment() {
      const name = document.getElementById("tenant").value.trim();
      const type = document.getElementById("type").value;
      const amount = Number(document.getElementById("amount").value);
      const method = document.getElementById("method").value;
      const result = document.getElementById("result");

      if (!name || !Number.isFinite(amount) || amount <= 0) {
        result.textContent = "Enter a tenant name and a valid amount.";
        return;
      }

      result.innerHTML =
        "<h3>Payment Preview</h3>" +
        "<p>Tenant: " + escapeText(name) + "</p>" +
        "<p>Type: " + type + "</p>" +
        "<p>Amount: GH₵" + amount.toFixed(2) + "</p>" +
        "<p>Method: " + method + "</p>" +
        "<p>This is a preview only. No payment has been saved.</p>";
    }

    function escapeText(value) {
      const element = document.createElement("span");
      element.textContent = value;
      return element.innerHTML;
    }
  </script>
</body>
</html>

