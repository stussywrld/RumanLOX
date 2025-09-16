# RumanLOX
[index_Version2.html](https://github.com/user-attachments/files/22363023/index_Version2.html)
<!DOCTYPE html>
<html lang="kk">
<head>
  <meta charset="UTF-8">
  <title>Руманды ұруға барамыз карочи</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f9f6ff; margin: 0; padding: 20px; text-align: center; }
    h1 { color: #d2691e; }
    .btn { display: inline-block; margin: 10px; padding: 12px 18px; border: none; border-radius: 8px; background: #d2691e; color: #fff; font-size: 16px; cursor: pointer; transition: .2s; }
    .btn:hover { opacity: 0.85; }
    #result, #all-results { margin-top: 20px; font-weight: bold; color: #333; }
    input { padding: 10px; border: 1px solid #ccc; border-radius: 6px; width: 60%; margin-top: 10px; }
    ul { list-style: none; padding: 0; }
    li { background: #fff; margin: 5px auto; border-radius: 6px; max-width: 400px; padding: 8px; }
    #all-results { text-align: left; margin: 30px auto 0; max-width: 400px; }
    .info { margin: 20px auto; background: #ffeecc; padding: 18px; border-radius: 12px; max-width: 440px; box-shadow: 0 2px 8px #d2691e22; }
  </style>
</head>
<body>
  <h1>Rumanda uruga baramyz RSVP</h1>
  <div class="info">
    <b>⚡️ Мега оқиға! ⚡️</b><br>
    <br>
    <b>Күні:</b> Мектеп біткен соң<br>
    <b>Орыны:</b> Абай мектебінің туалеті (ең креативті gathering)<br>
    <br>
    Урудың басты шарты — көңіл, әзіл, күлкі!<br>
    <i>“Кім руға дайын? Кім туалетте топтасады?”</i><br>
    Әркім өз атын жазып, таңдауын белгіле!
  </div>
  <input type="text" id="name" placeholder="Атыңды енгіз (ник, лақап та жарайды)">
  <br>
  <button class="btn" onclick="submitRSVP('Барамын')">Барамын</button>
  <button class="btn" onclick="submitRSVP('Бармаймын')">Бармаймын</button>
  <button class="btn" onclick="submitRSVP('Жалғыз барамын')">Жалғыз барамын</button>
  <button class="btn" onclick="submitRSVP('Туалетте селфи жасаймын')">Туалетте селфи жасаймын</button>
  <div id="result"></div>
  <div id="all-results">
    <h2>Барлық жауаптар:</h2>
    <ul id="results-list"></ul>
  </div>
  <script>
    const rsvpResults = [];
    function submitRSVP(choice) {
      const name = document.getElementById('name').value.trim();
      if (!name) {
        alert("Алдымен атыңды жаз!");
        return;
      }
      const idx = rsvpResults.findIndex(item => item.name === name);
      if (idx !== -1) {
        rsvpResults[idx].choice = choice;
      } else {
        rsvpResults.push({name, choice});
      }
      let funMsg = '';
      if (choice === 'Туалетте селфи жасаймын') {
        funMsg = "📸 Дайын бол, Инстаға саламыз!";
      }
      else if (choice === 'Барамын') {
        funMsg = "🔥 Ру үшін бәріне дайын!";
      }
      else if (choice === 'Бармаймын') {
        funMsg = "😢 Саған руманда орын жоқ...";
      }
      else if (choice === 'Жалғыз барамын') {
        funMsg = "🕺 Тығыз туалет, жалғыздықта ру!";
      }
      document.getElementById('result').innerText = name + " таңдады: " + choice + " " + funMsg;
      renderResults();
      document.getElementById('name').value = '';
    }
    function renderResults() {
      const list = document.getElementById('results-list');
      list.innerHTML = '';
      rsvpResults.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name}: ${item.choice}`;
        list.appendChild(li);
      });
    }
  </script>
  <div style="margin-top:40px;">
    <b>Сайт ашылған соң, сілтемені басқаларға жібере аласыз!</b><br>
    <span style="font-size: 14px; color: #999;">
      Барлық жауаптар тек осы бетте көрсетіледі.<br>
      Егер жауаптарды интернет арқылы жинағыңыз келсе, қосымша сервер немесе Google Forms керек.
    </span>
  </div>
</body>
</html>
