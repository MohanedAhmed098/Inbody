<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حاسبة الاحتياجات اليومية</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 20px;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 0 auto;
        }
        h1 {
            color: #333;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #28a745;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>حاسبة الاحتياجات اليومية</h1>
        
        <label for="weight">الوزن (كجم):</label>
        <input type="number" id="weight" placeholder="أدخل وزنك">
        
        <label for="activity">مستوى النشاط:</label>
        <select id="activity">
            <option value="1.2">قليل النشاط (لا تمارين)</option>
            <option value="1.375">خفيف النشاط (تمارين خفيفة)</option>
            <option value="1.55">متوسط النشاط (تمارين متوسطة)</option>
            <option value="1.725">عالي النشاط (تمارين مكثفة)</option>
            <option value="1.9">مكثف جدًا (تمارين شديدة)</option>
        </select>
        
        <button onclick="calculate()">احسب</button>
        
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculate() {
            const weight = parseFloat(document.getElementById('weight').value);
            const activity = parseFloat(document.getElementById('activity').value);

            if (isNaN(weight)) {
                alert("الرجاء إدخال وزن صحيح.");
                return;
            }

            // معادلات تقديرية (يمكن تعديلها حسب الحاجة)
            const protein = (weight * 0.8).toFixed(2); // بروتين
            const calories = (weight * 24 * activity).toFixed(2); // سعرات حرارية
            const carbs = (calories * 0.5 / 4).toFixed(2); // كربوهيدرات (50% من السعرات)
            const fat = (calories * 0.3 / 9).toFixed(2); // دهون (30% من السعرات)
            const water = (weight * 0.035).toFixed(2); // لتر ماء

            const result = `
                <p>البروتين: ${protein} جرام</p>
                <p>الكربوهيدرات: ${carbs} جرام</p>
                <p>الدهون الصحية: ${fat} جرام</p>
                <p>الماء: ${water} لتر</p>
            `;

            document.getElementById('result').innerHTML = result;
        }
    </script>

</body>
</html>
