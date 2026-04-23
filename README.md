<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Forma</title>

<style>
body {
    margin: 0;
    font-family: "Segoe UI", sans-serif;
    background: #0f172a;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #e5e7eb;
}

.container {
    background: rgba(255,255,255,0.03);
    backdrop-filter: blur(15px);
    padding: 35px;
    border-radius: 20px;
    width: 95%;
    max-width: 420px;
    box-shadow: 0 0 40px rgba(0,0,0,0.6);
}

h2 {
    margin-bottom: 25px;
    font-weight: 500;
    text-align: center;
    letter-spacing: 1px;
}

input {
    width: 100%;
    padding: 14px;
    margin: 10px 0;
    border-radius: 10px;
    border: 1px solid rgba(255,255,255,0.1);
    background: rgba(255,255,255,0.05);
    color: white;
    font-size: 15px;
    outline: none;
    transition: 0.25s;
}

input:focus {
    border-color: #6366f1;
    box-shadow: 0 0 10px rgba(99,102,241,0.6);
}

button {
    width: 100%;
    padding: 14px;
    margin-top: 15px;
    border: none;
    border-radius: 10px;
    background: #6366f1;
    color: white;
    font-size: 16px;
    cursor: pointer;
    transition: 0.25s;
}

button:hover {
    background: #4f46e5;
    box-shadow: 0 0 15px rgba(99,102,241,0.7);
}

.success {
    margin-top: 15px;
    text-align: center;
    color: #22c55e;
    display: none;
    font-size: 14px;
}
</style>

</head>
<body>

<div class="container">
    <h2>Ma'lumot kiriting</h2>

    <input type="text" id="name" placeholder="ismingiz">
    <input type="text" id="surname" placeholder="familangiz">

    <button onclick="sendData()">Royxatdan oʻtish</button>

    <div class="success" id="msg">Yuborildi ✔</div>
</div>

<script>
function sendData() {
    let name = document.getElementById("name").value;
    let surname = document.getElementById("surname").value;

    if(name === "" || surname === ""){
        alert("Iltimos, hamma joyni to'ldiring!");
        return;
    }

    let message = "ism: " + name + "%0AFamila: " + surname;

    let token = "8631542060:AAGOEigu9AABD6DrmQUya0hr4YlwI3FEINU";
    let chat_id = "8191019794";

    let url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chat_id}&text=${message}`;

    fetch(url)
    .then(() => {
        document.getElementById("msg").style.display = "block";
    })
    .catch(() => {
        alert("Xatolik yuz berdi");
    });
}
</script>

</body>
</html>
