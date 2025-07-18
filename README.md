<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>OAU Aggregate Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: #f4f4f4;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .input-group {
            margin: 10px 0;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input, select {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
        }
        button {
            background-color: #28a745;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
            color: #dc3545;
        }
        #date-time {
            text-align: center;
            font-style: italic;
            color: #666;
            margin-bottom: 20px;
        }
        .note {
            text-align: center;
            font-style: italic;
            color: #666;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>OAU Aggregate Calculator</h1>
    <div id="date-time">Generated on: Friday, July 18, 2025, 05:20 PM WAT</div>
    <div class="input-group">
        <label for="jamb">JAMB Score (0-400):</label>
        <input type="number" id="jamb" min="0" max="400" placeholder="Enter JAMB Score">
    </div>
    <div class="input-group">
        <label>O'Level Grades (Best 5 Subjects):</label>
        <select id="sub1"><option value="0">Select Grade</option><option value="10">A1</option><option value="9">B2</option><option value="8">B3</option><option value="7">C4</option><option value="6">C5</option><option value="5">C6</option></select>
        <select id="sub2"><option value="0">Select Grade</option><option value="10">A1</option><option value="9">B2</option><option value="8">B3</option><option value="7">C4</option><option value="6">C5</option><option value="5">C6</option></select>
        <select id="sub3"><option value="0">Select Grade</option><option value="10">A1</option><option value="9">B2</option><option value="8">B3</option><option value="7">C4</option><option value="6">C5</option><option value="5">C6</option></select>
        <select id="sub4"><option value="0">Select Grade</option><option value="10">A1</option><option value="9">B2</option><option value="8">B3</option><option value="7">C4</option><option value="6">C5</option><option value="5">C6</option></select>
        <select id="sub5"><option value="0">Select Grade</option><option value="10">A1</option><option value="9">B2</option><option value="8">B3</option><option value="7">C4</option><option value="6">C5</option><option value="5">C6</option></select>
    </div>
    <button onclick="calculateAggregate()">Calculate Aggregate</button>
    <div id="result"></div>
    <div class="note">Note: Post-UTME has not been conducted. Current aggregate is out of 60 (JAMB 50% + O'Level 10%). The remaining 40% will be added after PUTME.</div>

    <script>
        function calculateAggregate() {
            let jamb = parseFloat(document.getElementById('jamb').value);
            let sub1 = parseFloat(document.getElementById('sub1').value);
            let sub2 = parseFloat(document.getElementById('sub2').value);
            let sub3 = parseFloat(document.getElementById('sub3').value);
            let sub4 = parseFloat(document.getElementById('sub4').value);
            let sub5 = parseFloat(document.getElementById('sub5').value);

            if (isNaN(jamb) || jamb < 0 || jamb > 400) {
                document.getElementById('result').innerText = "Please enter a valid JAMB score (0-400).";
                return;
            }
            if (sub1 === 0 || sub2 === 0 || sub3 === 0 || sub4 === 0 || sub5 === 0) {
                document.getElementById('result').innerText = "Please select grades for all 5 subjects.";
                return;
            }

            let jambScore = jamb / 8; // 50% of JAMB
            let olevelScore = (sub1 + sub2 + sub3 + sub4 + sub5) / 5; // 10% of O'Level

            let aggregate = jambScore + olevelScore; // Current aggregate out of 60

            document.getElementById('result').innerText = `Your Current OAU Aggregate Score (out of 60) is: ${aggregate.toFixed(2)}`;
        }
    </script>
</body>
</html>
