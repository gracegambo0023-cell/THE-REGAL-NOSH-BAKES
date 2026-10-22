<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Regal Nosh | Digital Menu</title>
    <style>
        :root {
            --regal-plum: #5c0632;
            --royal-gold: #d4af37;
            --soft-cream: #fdfbf7;
            --dark-charcoal: #2d2d2d;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--soft-cream);
            color: var(--dark-charcoal);
            line-height: 1.6;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background: #fff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            border-top: 8px solid var(--regal-plum);
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px dashed var(--royal-gold);
            padding-bottom: 20px;
        }

        header h1 {
            color: var(--regal-plum);
            font-size: 28px;
            margin-bottom: 5px;
        }

        header p {
            font-style: italic;
            color: #666;
            font-size: 14px;
        }

        .notice {
            background-color: #fff9e6;
            border-left: 4px solid var(--royal-gold);
            padding: 10px;
            margin-bottom: 25px;
            font-size: 13px;
            border-radius: 4px;
        }

        .menu-item {
            display: flex;
            flex-direction: column;
            gap: 10px;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }

        .item-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .item-name {
            font-weight: bold;
            color: var(--regal-plum);
        }

        .item-controls {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 10px;
        }

        select, input {
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 14px;
            outline: none;
        }

        select:focus, input:focus {
            border-color: var(--regal-plum);
        }

        .item-total {
            text-align: right;
            font-size: 13px;
            color: #777;
            font-weight: 600;
        }

        .basket-summary {
            margin-top: 30px;
            padding: 20px;
            background: #f9f3f6;
            border-radius: 8px;
            border: 1px solid #ebd9e2;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            font-size: 20px;
            font-weight: bold;
            color: var(--regal-plum);
            margin-bottom: 20px;
        }

        .btn-checkout {
            display: block;
            width: 100%;
            background-color: #25D366;
            color: white;
            text-align: center;
            padding: 14px;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            text-decoration: none;
            transition: background 0.3s;
        }

        .btn-checkout:hover {
            background-color: #128C7E;
        }

        footer {
            text-align: center;
            margin-top: 30px;
            font-size: 12px;
            color: #888;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>👑 The Regal Nosh</h1>
        <p>A Taste of Royalty • Freshly made with love, specially for you.</p>
    </header>

    <div class="notice">
        <strong>Please Note:</strong> Celebration Cakes require direct consultation for pricing. Kindly confirm final estimates before booking.
    </div>

    <form id="menuForm">
        <!-- Chinchin -->
        <div class="menu-item" data-product="Chinchin">
            <div class="item-info">
                <span class="item-name">Chinchin</span>
                <span class="item-total" id="total-chinchin">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="4500" data-label="1 Litre">1 Litre (₦4,500)</option>
                    <option value="18000" data-label="4 Litres">4 Litres (₦18,000)</option>
                    <option value="85000" data-label="20 Litres">20 Litres (₦85,000)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Celebration Cakes -->
        <div class="menu-item" data-product="Celebration Cakes">
            <div class="item-info">
                <span class="item-name">Celebration Cakes</span>
                <span class="item-total" id="total-cakes">Price on request</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="0" data-label="Inquire via WhatsApp">Inquire via WhatsApp</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Meat Pies -->
        <div class="menu-item" data-product="Meat Pies">
            <div class="item-info">
                <span class="item-name">Meat Pies</span>
                <span class="item-total" id="total-meatpies">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1000" data-label="1 Piece">1 Piece (₦1,000)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Small Chops -->
        <div class="menu-item" data-product="Small Chops">
            <div class="item-info">
                <span class="item-name">Small Chops</span>
                <span class="item-total" id="total-smallchops">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1000" data-label="Standard Pack">Standard Pack (₦1,000)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Cake Parfait -->
        <div class="menu-item" data-product="Cake Parfait">
            <div class="item-info">
                <span class="item-name">Cake Parfait</span>
                <span class="item-total" id="total-parfait">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1500" data-label="Standard Cup">Standard Cup (₦1,500)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Zobo -->
        <div class="menu-item" data-product="Zobo">
            <div class="item-info">
                <span class="item-name">Zobo</span>
                <span class="item-total" id="total-zobo">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1000" data-label="Standard Bottle">Standard Bottle (₦1,000)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Tigernut Drink / Kunu Aya (MERGED CATEGORY) -->
        <div class="menu-item" data-product="Tigernut Drink (Kunu Aya)">
            <div class="item-info">
                <span class="item-name">Tigernut Drink (Kunu Aya)</span>
                <span class="item-total" id="total-kunu">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1500" data-label="Standard Bottle">Standard Bottle (₦1,500)</option>
                    <option value="4500" data-label="Large Pack">Large Pack (₦4,500)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <!-- Soya Milk -->
        <div class="menu-item" data-product="Soya Milk">
            <div class="item-info">
                <span class="item-name">Soya Milk</span>
                <span class="item-total" id="total-soya">₦0</span>
            </div>
            <div class="item-controls">
                <select class="item-option" onchange="calculateTotal()">
                    <option value="1000" data-label="Standard Bottle">Standard Bottle (₦1,000)</option>
                </select>
                <input type="number" class="item-qty" min="0" value="0" placeholder="Qty" oninput="calculateTotal()">
            </div>
        </div>

        <div class="basket-summary">
            <div class="total-row">
                <span>Total Basket:</span>
                <span id="grandTotal">₦0</span>
            </div>
