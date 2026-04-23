script>
<!DOCTYPE html>
<html lang="ku">
<head>
  <meta charset="UTF-8" />
  <title>فۆرمی قەرزی پەنزین و گازوایل</title>
</head>
<body>
  <h2>📝 فۆرمی قەرزی پەنزین و گازوایل</h2>

  <form id="creditForm">
    <label>👤 ناوی کەسەکە:</label><br />
    <input type="text" id="personName" placeholder="مثال: سی قۆڵی" required /><br /><br />

    <label>🔢 ژمارەی ئۆتۆمبیل:</label><br />
    <input type="text" id="carNumber" required /><br /><br />

    <label>🚘 جۆری ئۆتۆمبیل:</label><br />
    <select id="carType">
      <option value="سیارە">سیارە</option>
      <option value="قالەب">قالەب</option>
      <option value="تلیرە">تلیرە</option>
    </select><br /><br />

    <label>⛽ جۆری سوتوەر:</label><br />
    <select id="fuelType" required>
      <option value="">-- هەلبژێرە --</option>
      <option value="پەنزین">پەنزین</option>
      <option value="گازوایل">گازوایل</option>
    </select><br /><br />

    <label>⛽ ژمارەی لەترەکان:</label><br />
    <input type="number" id="liters" required /><br /><br />

    <label>💰 نرخی هر لەتر (دینار):</label><br />
    <input type="number" id="pricePerLiter" step="1" readonly /><br /><br />

    <button type="submit">📤 ناردن بۆ تێلەگرام</button>
  </form>

  <p id="status"></p>

  <script>
    const TOKEN = "6353613680:AAHzPeD0V07eCbxK4O7MtXdFtkIa0yM9d6Y";
    const CHAT_ID = 2121432089;

    const pricePetrol = 875;  // نرخ پەنزین
    const priceDiesel = 525;  // نرخ گازوایل

    const fuelTypeSelect = document.getElementById("fuelType");
    const priceInput = document.getElementById("pricePerLiter");

    fuelTypeSelect.addEventListener("change", () => {
      if (fuelTypeSelect.value === "پەنزین") {
        priceInput.value = pricePetrol;
      } else if (fuelTypeSelect.value === "گازوایل") {
        priceInput.value = priceDiesel;
      } else {
        priceInput.value = "";
      }
    });

    document.getElementById("creditForm").addEventListener("submit", async function (e) {
      e.preventDefault();

      const name = document.getElementById("personName").value;
      const carNumber = document.getElementById("carNumber").value;
      const carType = document.getElementById("carType").value;
      const fuelType = document.getElementById("fuelType").value;
      const liters = parseFloat(document.getElementById("liters").value);
      const pricePerLiter = parseFloat(document.getElementById("pricePerLiter").value);

      if (!fuelType) {
        alert("تکایە جۆری سوتوەر هەلبژێرە");
        return;
      }

      const totalIQD = Math.round(liters * pricePerLiter);

      const today = new Date().toLocaleDateString("ku-IQ");

      const message = 📌 قەرزی سوتوەر:\n👤 ناو: ${name}\n🔢 ژمارەی ئۆتۆمبیل: ${carNumber}\n🚘 جۆری ئۆتۆمبیل: ${carType}\n⛽ جۆری سوتوەر: ${fuelType}\n⛽ ژمارەی لەتر: ${liters}\n💰 نرخی هر لەتر: ${pricePerLiter} دینار\n💰 کۆی گشتی: ${totalIQD.toLocaleString()} دینار\n📅 بەروار: ${today};

      try {
        const response = await fetch(`https://api.telegram.org/bot${TOKEN}/sendMessage`, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            chat_id: CHAT_ID,
            text: message,
          }),
        });

        document.getElementById("status").innerText = response.ok
          ? "✅ زانیاری نێردرا بۆ تێلەگرام."
          : "❌ هەڵەیەک ڕوویدا لە ناردن.";
      } catch (error) {
        document.getElementById("status").innerText = "❌ کێشەی تۆڕ.";
        console.error(error);
      }
    });
  </script>
</body>
</html>
