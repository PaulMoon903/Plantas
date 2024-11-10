
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>App de Riego de Plantas</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <style>
        .plant-image {
            height: 200px;
            width: 200px;
            object-fit: cover;
            border-radius: 0.5rem;
        }
    </style>
</head>
<body class="bg-green-100 font-sans leading-normal tracking-normal">
    <div class="container mx-auto px-4 py-6">
        <h1 class="text-3xl font-bold text-center text-green-700 mb-6">App de Riego de Plantas</h1>

        <!-- Información de las plantas -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
            <!-- Poto -->
            <div class="bg-white p-4 rounded-lg shadow-md text-center">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Pothos_NJoy.jpg/640px-Pothos_NJoy.jpg" alt="Poto" class="plant-image mx-auto">
                <h2 class="text-xl font-semibold text-green-700 mt-4">Poto</h2>
                <p class="text-gray-600">Frecuencia de riego: Cada 1-2 semanas</p>
                <button onclick="waterPlant('poto')" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4">Regar</button>
                <p id="poto-last-watered" class="text-gray-600 mt-2"></p>
            </div>
            <!-- Sanseviera -->
            <div class="bg-white p-4 rounded-lg shadow-md text-center">
                <img src="https://upload.wikimedia.org/wikipedia/commons/3/33/Sansevieria_trifasciata_cv._Laurentii.jpg" alt="Sanseviera" class="plant-image mx-auto">
                <h2 class="text-xl font-semibold text-green-700 mt-4">Sanseviera</h2>
                <p class="text-gray-600">Frecuencia de riego: Cada 2-6 semanas</p>
                <button onclick="waterPlant('sanseviera')" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4">Regar</button>
                <p id="sanseviera-last-watered" class="text-gray-600 mt-2"></p>
            </div>
            <!-- Costilla de Adán -->
            <div class="bg-white p-4 rounded-lg shadow-md text-center">
                <img src="[https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Monstera_deliciosa.JPG/1200px-Monstera_deliciosa.JPG" alt="Costilla de Adán" class="plant-image mx-auto](https://media.vogue.es/photos/601412d18b46611ae2f9a563/2:3/w_2560%2Cc_limit/monstera2.jpg)">
                <h2 class="text-xl font-semibold text-green-700 mt-4">Costilla de Adán</h2>
                <p class="text-gray-600">Frecuencia de riego: Cada semana</p>
                <button onclick="waterPlant('costilla')" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4">Regar</button>
                <p id="costilla-last-watered" class="text-gray-600 mt-2"></p>
            </div>
        </div>
    </div>

    <script>
        // Cargar la última fecha de riego de cada planta
        function loadWateringDates() {
            const plants = ['poto', 'sanseviera', 'costilla'];
            plants.forEach(plant => {
                const lastWatered = localStorage.getItem(plant + '-lastWatered');
                if (lastWatered) {
                    document.getElementById(plant + '-last-watered').innerText = 'Último riego: ' + lastWatered;
                }
            });
        }

        // Actualizar la fecha de riego de una planta y guardarla en localStorage
        function waterPlant(plant) {
            const currentDate = new Date().toLocaleDateString();
            localStorage.setItem(plant + '-lastWatered', currentDate);
            document.getElementById(plant + '-last-watered').innerText = 'Último riego: ' + currentDate;
        }

        // Cargar fechas de riego al iniciar la app
        document.addEventListener('DOMContentLoaded', loadWateringDates);
    </script>
</body>
</html>
