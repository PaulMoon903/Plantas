<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seguimiento de Riego de Plantas</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gradient-to-r from-green-200 to-blue-200 text-gray-800 flex items-center justify-center min-h-screen">
    <div class="w-full max-w-md p-8 bg-white rounded-lg shadow-lg border border-gray-300">
        <h1 class="text-3xl font-bold text-center mb-8 text-green-600">Registro de Riego de Plantas</h1>
        
        <div class="space-y-6">
            <!-- Potos -->
            <div class="flex items-center justify-between">
                <div class="flex items-center">
                    <img src="https://cdn.pixabay.com/photo/2019/11/04/00/11/pothos-4592861_1280.jpg" alt="Potos" class="rounded-full w-12 h-12 mr-4">
                    <div>
                        <h2 class="text-lg font-semibold">Potos</h2>
                        <p class="text-sm text-gray-500">Riego cada 7 días</p>
                        <p class="text-xs text-gray-400 mt-1">Último riego: <span id="potos-fecha" class="font-semibold">No registrado</span></p>
                    </div>
                </div>
                <button onclick="registraRiego('potos')" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-md font-semibold">
                    Regar
                </button>
            </div>

            <!-- Sansevieria -->
            <div class="flex items-center justify-between">
                <div class="flex items-center">
                    <img src="https://cdn.pixabay.com/photo/2020/08/13/13/06/snake-plant-5485679_1280.jpg" alt="Sansevieria" class="rounded-full w-12 h-12 mr-4">
                    <div>
                        <h2 class="text-lg font-semibold">Sansevieria</h2>
                        <p class="text-sm text-gray-500">Riego cada 14 días</p>
                        <p class="text-xs text-gray-400 mt-1">Último riego: <span id="sansevieria-fecha" class="font-semibold">No registrado</span></p>
                    </div>
                </div>
                <button onclick="registraRiego('sansevieria')" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-md font-semibold">
                    Regar
                </button>
            </div>

            <!-- Costilla de Adán -->
            <div class="flex items-center justify-between">
                <div class="flex items-center">
                    <img src="https://cdn.pixabay.com/photo/2018/02/13/00/27/monstera-3149358_1280.jpg" alt="Costilla de Adán" class="rounded-full w-12 h-12 mr-4">
                    <div>
                        <h2 class="text-lg font-semibold">Costilla de Adán</h2>
                        <p class="text-sm text-gray-500">Riego cada 10 días</p>
                        <p class="text-xs text-gray-400 mt-1">Último riego: <span id="costilla-fecha" class="font-semibold">No registrado</span></p>
                    </div>
                </div>
                <button onclick="registraRiego('costilla')" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-md font-semibold">
                    Regar
                </button>
            </div>
        </div>
    </div>

    <script>
        // Intervalos recomendados para riego en días
        const intervalosRiego = {
            potos: 7, // cada semana
            sansevieria: 14, // cada dos semanas
            costilla: 10 // cada 10 días
        };

        // Función para actualizar la fecha de riego en la interfaz
        function actualizaFechaRiego(planta) {
            const fecha = localStorage.getItem(`riego-${planta}`);
            const fechaElemento = document.getElementById(`${planta}-fecha`);
            fechaElemento.innerText = fecha ? new Date(fecha).toLocaleDateString() : "No registrado";
        }

        // Registrar la fecha de riego en localStorage
        function registraRiego(planta) {
            const fechaActual = new Date();
            localStorage.setItem(`riego-${planta}`, fechaActual);
            actualizaFechaRiego(planta);
            alert(`Has regado la planta ${planta.charAt(0).toUpperCase() + planta.slice(1)}.`);
        }

        // Inicialización: cargar fechas de riego desde localStorage
        document.addEventListener("DOMContentLoaded", () => {
            actualizaFechaRiego('potos');
            actualizaFechaRiego('sansevieria');
            actualizaFechaRiego('costilla');
        });
    </script>
</body>
</html>
