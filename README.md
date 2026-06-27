# Phonk-hub-
Lising to all the best phonks
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Free Music Player</title>

<style>
body{
    margin:0;
    background:#0d0d0d;
    color:white;
    font-family:Arial;
    text-align:center;
}
input{
    width:80%;
    padding:12px;
    margin:20px;
    border:none;
    border-radius:10px;
}
img{
    width:250px;
    border-radius:15px;
    margin:20px;
}
audio{
    width:90%;
}
button{
    padding:10px 20px;
    border:none;
    border-radius:10px;
    cursor:pointer;
}
</style>

</head>
<body>

<h1>🎵 Free Music Player</h1>

<input id="search" placeholder="Buscar canción">
<button onclick="buscar()">Buscar</button>

<div id="resultado"></div>

<script>

const CLIENT_ID="TU_CLIENT_ID";

async function buscar(){

const texto=document.getElementById("search").value;

const url=`https://api.jamendo.com/v3.0/tracks/?client_id=${CLIENT_ID}&format=json&limit=1&search=${texto}&audioformat=mp31`;

const data=await fetch(url).then(r=>r.json());

if(data.results.length==0){
document.getElementById("resultado").innerHTML="No encontrado";
return;
}

const song=data.results[0];

document.getElementById("resultado").innerHTML=`
<h2>${song.name}</h2>
<h3>${song.artist_name}</h3>

<img src="${song.image}">

<br>

<audio controls src="${song.audio}"></audio>

`;

}

</script>

</body>
</html>
