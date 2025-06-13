<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Water Bill Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #d9efff;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 30px auto;
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 30px;
        }
        h1, p {
            text-align: center;
            color: #0073cf;
        }
        select, input, button {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            margin-bottom: 20px;
            border-radius: 6px;
            border: 1px solid #ccc;
            font-size: 16px;
        }
        button {
            background-color: #1a90ff;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }
        .result {
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            color: #1a4dab;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 30px;
        }
        th, td {
            padding: 12px;
            text-align: center;
            border: 1px solid #ccc;
        }
        th {
            background-color: #bde3ff;
            color: #003b80;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Water Bill Calculator</h1>
        <p>Calculate your water bill based on consumption and classification</p>

        <label for="classification">Select Classification</label>
        <select id="classification">
            <option value="residential">Residential (1/2)</option>
        </select>

        <label for="consumption">Enter Consumption (m³)</label>
        <input type="number" id="consumption" value="13">

        <button onclick="calculateBill()">Calculate</button>

        <div class="result" id="result">Estimated Water Bill: $310.80</div>

        <table>
            <thead>
                <tr>
                    <th>Classification</th>
                    <th>1-10 m³</th>
                    <th>11-20 m³</th>
                    <th>21-30 m³</th>
                    <th>31-40 m³</th>
                    <th>40 m³ and above</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Residential (1/2)</td>
                    <td>237.00</td>
                    <td>24.60</td>
                    <td>25.90</td>
                    <td>28.05</td>
                    <td>31.25</td>
                </tr>
                <tr>
                    <td>Commercial A (1/2)</td>
                    <td>414.47</td>
                    <td>23.05</td>
                    <td>45.30</td>
                    <td>49.05</td>
                    <td>54.65</td>
                </tr>
                <tr>
                    <td>Commercial B (1/2)</td>
                    <td>355.50</td>
                    <td>36.90</td>
                    <td>38.85</td>
                    <td>42.05</td>
                    <td>46.85</td>
                </tr>
                <tr>
                    <td>Commercial C (1/2)</td>
                    <td>296.25</td>
                    <td>30.75</td>
                    <td>32.35</td>
                    <td>35.05</td>
                    <td>39.05</td>
                </tr>
                <tr>
                    <td>Full Commercial (1/2)</td>
                    <td>474.00</td>
                    <td>49.20</td>
                    <td>51.80</td>
                    <td>56.10</td>
                    <td>62.50</td>
                </tr>
            </tbody>
        </table>
    </div>

    <script>
        function calculateBill() {
            const consumption = parseFloat(document.getElementById("consumption").value);
            let total = 0;

            if (consumption <= 10) {
                total = 237.00;
            } else {
                total = 237.00;
                let remaining = consumption - 10;

                if (remaining > 0) {
                    let tier2 = Math.min(10, remaining);
                    total += tier2 * 24.60;
                    remaining -= tier2;
                }
                if (remaining > 0) {
                    let tier3 = Math.min(10, remaining);
                    total += tier3 * 25.90;
                    remaining -= tier3;
                }
                if (remaining > 0) {
                    let tier4 = Math.min(10, remaining);
                    total += tier4 * 28.05;
                    remaining -= tier4;
                }
                if (remaining > 0) {
                    total += remaining * 31.25;
                }
            }

            document.getElementById("result").textContent = `Estimated Water Bill: $${total.toFixed(2)}`;
        }
    </script>
</body>
</html>
