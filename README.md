<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MotoExpress - Sistema de Mototaxi Inteligente</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:#f8fafc;
color:#333;
}

header{
height:100vh;
background:linear-gradient(rgba(0,0,0,.55),rgba(0,0,0,.55)),
url('https://images.unsplash.com/photo-1511919884226-fd3cad34687c?w=1600');
background-size:cover;
background-position:center;
display:flex;
justify-content:center;
align-items:center;
text-align:center;
color:white;
}

.hero h1{
font-size:4rem;
margin-bottom:15px;
}

.hero span{
color:#FFD60A;
}

.hero p{
font-size:1.2rem;
max-width:700px;
margin:auto;
margin-bottom:30px;
}

.btn{
background:#FFD60A;
color:#000;
padding:15px 35px;
border-radius:50px;
text-decoration:none;
font-weight:600;
transition:0.3s;
}

.btn:hover{
transform:translateY(-5px);
}

section{
padding:80px 10%;
}

.titulo{
text-align:center;
font-size:2.5rem;
margin-bottom:50px;
color:#0A2540;
}

.servicios{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:25px;
}

.card{
background:white;
padding:30px;
border-radius:20px;
box-shadow:0 10px 25px rgba(0,0,0,.1);
transition:.3s;
}

.card:hover{
transform:translateY(-10px);
}

.card h3{
color:#198754;
margin-bottom:15px;
}

.estadisticas{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
gap:20px;
margin-top:40px;
}

.stat{
background:#198754;
color:white;
padding:30px;
border-radius:20px;
text-align:center;
}

.stat h2{
font-size:2.5rem;
}

.calculadora{
max-width:700px;
margin:auto;
background:white;
padding:40px;
border-radius:25px;
box-shadow:0 10px 30px rgba(0,0,0,.15);
}

input,select{
width:100%;
padding:15px;
margin-top:10px;
margin-bottom:20px;
border:1px solid #ddd;
border-radius:10px;
}

button{
width:100%;
padding:15px;
background:#198754;
color:white;
border:none;
border-radius:10px;
font-size:18px;
cursor:pointer;
}

button:hover{
background:#146c43;
}

.resultado{
margin-top:20px;
padding:20px;
background:#f1f8f4;
border-radius:15px;
font-weight:600;
}

footer{
background:#0A2540;
color:white;
text-align:center;
padding:25px;
}

</style>
</head>

<body>

<header>

<div class="hero">

<h1>🛵 <span>MotoExpress</span></h1>

<p>
Sistema Inteligente de Mototaxis para viajes rápidos, seguros y económicos.
Calcula tarifas automáticamente, aplica descuentos y administra ganancias.
</p>

<a href="#calculadora" class="btn">Calcular Viaje</a>

</div>

</header>

<section>

<h2 class="titulo">Nuestros Servicios</h2>

<div class="servicios">

<div class="card">
<h3>🛵 Transporte Urbano</h3>
<p>Viajes rápidos dentro de la ciudad con conductores verificados.</p>
</div>

<div class="card">
<h3>⏱️ Reserva Inmediata</h3>
<p>Solicita una mototaxi en segundos desde cualquier lugar.</p>
</div>

<div class="card">
<h3>🎁 Cliente Frecuente</h3>
<p>Obtén descuentos especiales por usar constantemente el servicio.</p>
</div>

<div class="card">
<h3>🔒 Seguridad</h3>
<p>Monitoreo de viajes y conductores registrados.</p>
</div>

</div>

</section>

<section>

<h2 class="titulo">Estadísticas</h2>

<div class="estadisticas">

<div class="stat">
<h2>5000+</h2>
<p>Viajes Realizados</p>
</div>

<div class="stat">
<h2>200+</h2>
<p>Conductores</p>
</div>

<div class="stat">
<h2>98%</h2>
<p>Satisfacción</p>
</div>

<div class="stat">
<h2>24/7</h2>
<p>Disponibilidad</p>
</div>

</div>

</section>

<section id="calculadora">

<h2 class="titulo">Calculadora de Tarifas</h2>

<div class="calculadora">

<label>Distancia del viaje (Km)</label>
<input type="number" id="distancia" placeholder="Ejemplo: 5">

<label>Minutos de espera</label>
<input type="number" id="espera" placeholder="Ejemplo: 3">

<label>Cliente frecuente</label>
<select id="cliente">
<option value="no">No</option>
<option value="si">Sí (20% descuento)</option>
</select>

<button onclick="calcular()">Calcular Tarifa</button>

<div class="resultado" id="resultado">
Ingrese los datos para calcular el costo del viaje.
</div>

</div>

</section>

<footer>

<h3>MotoExpress 🛵</h3>
<p>Proyecto Universitario - Sistema de Gestión de Mototaxis</p>

</footer>

<script>

function calcular(){

let distancia = parseFloat(document.getElementById("distancia").value) || 0;
let espera = parseFloat(document.getElementById("espera").value) || 0;

let tarifaBase = distancia * 1.50;
let costoEspera = espera * 2.50;

let total = tarifaBase + costoEspera;

if(document.getElementById("cliente").value === "si"){
total = total * 0.80;
}

let conductor = total * 0.90;
let empresa = total * 0.10;

document.getElementById("resultado").innerHTML =
`
💰 Total a pagar: <b>S/ ${total.toFixed(2)}</b><br><br>

🛵 Ganancia del conductor (90%): <b>S/ ${conductor.toFixed(2)}</b><br>

🏢 Comisión de la empresa (10%): <b>S/ ${empresa.toFixed(2)}</b>
`;

}

</script>

</body>
</html>
