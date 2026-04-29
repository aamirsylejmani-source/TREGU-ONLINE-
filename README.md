<!DOCTYPE html>
<html lang="sq">
<head>
<meta charset="UTF-8">
<title>TREGU ONLINE</title>

<style>
body {
    font-family: Arial;
    background: #f5f5f5;
    margin: 0;
}

header {
    background: #ff6600;
    color: white;
    padding: 15px;
    text-align: center;
}

.container {
    padding: 20px;
}

.form {
    background: white;
    padding: 15px;
    border-radius: 10px;
}

input, button {
    padding: 10px;
    margin: 5px;
}

button {
    background: #ff6600;
    color: white;
    border: none;
}

.card {
    background: white;
    margin-top: 15px;
    padding: 15px;
    border-radius: 10px;
}
</style>
</head>

<body>

<header>
    <h1>TREGU ONLINE - Makina</h1>
</header>

<div class="container">

    <div class="form">
        <input type="text" id="titulli" placeholder="Titulli (Audi A4)">
        <input type="number" id="cmimi" placeholder="Cmimi">
        <button onclick="shto()">Posto shpallje</button>
    </div>

    <div id="lista"></div>

</div>

<script>

let shpalljet = JSON.parse(localStorage.getItem("makinat")) || [];

function shfaq() {
    let lista = document.getElementById("lista");
    lista.innerHTML = "";

    shpalljet.forEach((m) => {
        lista.innerHTML += `
            <div class="card">
                <h3>${m.titulli}</h3>
                <p>Cmimi: ${m.cmimi} €</p>
            </div>
        `;
    });
}

function shto() {
    let titulli = document.getElementById("titulli").value;
    let cmimi = document.getElementById("cmimi").value;

    let obj = { titulli, cmimi };

    shpalljet.push(obj);

    localStorage.setItem("makinat", JSON.stringify(shpalljet));

    shfaq();
}

shfaq();

</script>

</body>
</html>
