# -Avistamiento-Masivo-de-OVNI-en-el-Desierto-de-Atacama-
pagina acerca de ovnis
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Noticia de OVNI - Avistamiento Misterioso</title>
    <!-- Enlace a Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            /* Establece un fondo muy oscuro para la página */
            background-color: #1a202c; /* Color de fondo oscuro */
            color: #e2e8f0; /* Color de texto claro */
        }
        .loading-spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top: 4px solid #a78bfa; /* Color morado */
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="flex items-center justify-center min-h-screen p-4">
    <div class="max-w-4xl w-full bg-gray-800 rounded-lg shadow-xl p-8 md:p-12 border border-gray-700">
        <!-- Título principal de la noticia -->
        <h1 class="text-4xl md:text-5xl font-bold text-center text-purple-400 mb-6 leading-tight">
            ¡Avistamiento Masivo de OVNI en el Desierto de Atacama!
        </h1>

        <!-- Fecha y autor (ficticios) -->
        <p class="text-sm text-gray-400 text-center mb-8">
            Publicado el 11 de Julio de 2025 por: El Observador Cósmico
        </p>

        <!-- Contenedor de la imagen principal con spinner de carga -->
        <div id="main-image-container" class="flex justify-center items-center mb-8 bg-gray-700 rounded-lg shadow-lg" style="min-height: 250px;">
            <div class="loading-spinner" id="main-image-spinner"></div>
            <img id="main-ufo-image" src="" alt="Imagen de un OVNI en el cielo nocturno"
                 class="rounded-lg shadow-lg border border-gray-600 w-full max-w-full h-auto hidden"
                 onerror="this.onerror=null;this.src='https://placehold.co/800x450/333/fff?text=Imagen+no+disponible'; this.classList.remove('hidden'); document.getElementById('main-image-spinner').classList.add('hidden');">
        </div>

        <!-- Cuerpo de la noticia falsa -->
        <div class="text-lg leading-relaxed mb-8 space-y-6">
            <p>
                Testigos en la remota región del Desierto de Atacama en Chile reportaron anoche un fenómeno aéreo sin precedentes. Múltiples fuentes describen la aparición de una formación de luces brillantes y silenciosas que se movían con una agilidad imposible para cualquier aeronave conocida.
            </p>
            <p>
                Los reportes iniciales, que comenzaron a inundar las redes sociales alrededor de las 22:00 horas, hablan de objetos con formas geométricas inusuales que permanecieron visibles durante casi una hora antes de desaparecer a una velocidad vertiginosa. "Nunca había visto algo así", afirmó María Elena Rojas, una astrónoma aficionada que presenció el evento desde su observatorio casero. "No era un satélite, ni un avión, ni ningún dron. Era... otra cosa."
            </p>
            <!-- Contenedor de la imagen del testigo con spinner de carga -->
            <div id="witness-image-container" class="flex justify-center items-center my-6 bg-gray-700 rounded-lg shadow-lg" style="min-height: 200px;">
                <div class="loading-spinner" id="witness-image-spinner"></div>
                <img id="witness-photo" src="" alt="Foto de un testigo con un fondo borroso"
                     class="rounded-lg shadow-md border border-gray-600 w-full max-w-xs h-auto hidden"
                     onerror="this.onerror=null;this.src='https://placehold.co/400x300/333/fff?text=Foto+testigo+no+disponible'; this.classList.remove('hidden'); document.getElementById('witness-image-spinner').classList.add('hidden');">
            </div>
            <p>
                Las autoridades locales aún no han emitido una declaración oficial, y los intentos de contactar a la Fuerza Aérea Chilena para obtener comentarios no han tenido éxito. Mientras tanto, la comunidad en línea está en ebullición, con videos de baja calidad y testimonios emocionados circulando rápidamente. ¿Estamos ante la primera evidencia irrefutable de vida extraterrestre, o es un elaborado engaño?
            </p>
        </div>

        <!-- Descargo de responsabilidad (importante para una noticia falsa) -->
        <div class="bg-red-900 bg-opacity-50 border border-red-700 rounded-md p-4 text-center text-red-200 text-sm italic">
            <p>
                <strong>AVISO:</strong> Esta es una noticia ficticia creada con fines de demostración y entretenimiento. Cualquier parecido con eventos reales es pura coincidencia.
            </p>
        </div>
    </div>

    <script>
        async function generateAndLoadImages() {
            const mainUfoImage = document.getElementById('main-ufo-image');
            const mainImageSpinner = document.getElementById('main-image-spinner');
            const witnessPhoto = document.getElementById('witness-photo');
            const witnessImageSpinner = document.getElementById('witness-image-spinner');

            // Show spinners
            mainImageSpinner.classList.remove('hidden');
            witnessImageSpinner.classList.remove('hidden');
            mainUfoImage.classList.add('hidden');
            witnessPhoto.classList.add('hidden');

            try {
                // Generate main UFO image
                const payloadUFO = { instances: { prompt: "UFO flying over the Atacama Desert at night, mysterious lights, sci-fi, realistic, high detail, dark sky, stars visible" }, parameters: { "sampleCount": 1} };
                const apiKey = ""; // If you want to use models other than imagen-3.0-generate-002, provide an API key here. Otherwise, leave this as-is.
                const apiUrlUFO = `https://generativelanguage.googleapis.com/v1beta/models/imagen-3.0-generate-002:predict?key=${apiKey}`;
                const responseUFO = await fetch(apiUrlUFO, {
                           method: 'POST',
                           headers: { 'Content-Type': 'application/json' },
                           body: JSON.stringify(payloadUFO)
                       });
                const resultUFO = await responseUFO.json();

                if (resultUFO.predictions && resultUFO.predictions.length > 0 && resultUFO.predictions[0].bytesBase64Encoded) {
                    const imageUrlUFO = `data:image/png;base64,${resultUFO.predictions[0].bytesBase64Encoded}`;
                    mainUfoImage.src = imageUrlUFO;
                    mainUfoImage.classList.remove('hidden');
                } else {
                    console.error("Error generating UFO image:", resultUFO);
                    mainUfoImage.onerror(); // Trigger fallback
                }

                // Generate witness photo
                const payloadWitness = { instances: { prompt: "Photo of a person looking surprised and pointing at something out of frame, blurry background, dark setting, realistic, low light" }, parameters: { "sampleCount": 1} };
                const apiUrlWitness = `https://generativelanguage.googleapis.com/v1beta/models/imagen-3.0-generate-002:predict?key=${apiKey}`;
                const responseWitness = await fetch(apiUrlWitness, {
                           method: 'POST',
                           headers: { 'Content-Type': 'application/json' },
                           body: JSON.stringify(payloadWitness)
                       });
                const resultWitness = await responseWitness.json();

                if (resultWitness.predictions && resultWitness.predictions.length > 0 && resultWitness.predictions[0].bytesBase64Encoded) {
                    const imageUrlWitness = `data:image/png;base64,${resultWitness.predictions[0].bytesBase64Encoded}`;
                    witnessPhoto.src = imageUrlWitness;
                    witnessPhoto.classList.remove('hidden');
                } else {
                    console.error("Error generating witness image:", resultWitness);
                    witnessPhoto.onerror(); // Trigger fallback
                }

            } catch (error) {
                console.error("Failed to generate images:", error);
                mainUfoImage.onerror(); // Trigger fallback for main image
                witnessPhoto.onerror(); // Trigger fallback for witness image
            } finally {
                // Hide spinners after attempt
                mainImageSpinner.classList.add('hidden');
                witnessImageSpinner.classList.add('hidden');
            }
        }

        // Call the function to generate and load images when the page loads
        window.onload = generateAndLoadImages;
    </script>
</body>
</html>

