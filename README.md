<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Misión Detective: Las Tres Mentiras</title>
    <style>
        :root { --p-morado: #e0aaff; --p-amarillo: #ffff00; --p-azul: #a2d2ff; --p-verde: #b7efc5; }
        body { font-family: 'Comic Sans MS', sans-serif; line-height: 1.6; color: #333; max-width: 850px; margin: 0 auto; padding: 20px; background-color: #f0f9ff; }
        .card { background: white; padding: 30px; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); border: 3px solid #3498db; }
        
        /* Herramientas de destacado */
        .toolbar { position: sticky; top: 10px; background: #fff; padding: 15px; border: 3px solid #3498db; border-radius: 15px; margin-bottom: 20px; display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; z-index: 100; box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .btn { border: 2px solid #555; padding: 10px 15px; border-radius: 10px; cursor: pointer; font-weight: bold; transition: 0.2s; }
        .btn-yellow { background: var(--p-amarillo); }
        .btn-blue { background: var(--p-azul); }
        .btn-purple { background: var(--p-morado); }
        .btn-clear { background: #ff4d4d; color: white; }
        
        .texto-lectura { font-size: 1.2em; background: #fff; padding: 25px; border-radius: 15px; border: 2px dashed #3498db; margin-bottom: 30px; }
        .pregunta { background: #fdfdfd; padding: 20px; border-radius: 15px; margin-bottom: 25px; border: 2px solid #ddd; }
        
        /* Retroalimentación Visual */
        .opcion { display: block; padding: 10px; margin: 5px 0; border: 1px solid #ccc; border-radius: 8px; cursor: pointer; transition: 0.3s; }
        .opcion:hover { background-color: #f0f0f0; }
        .correcta { background-color: #d4edda !important; border-color: #c3e6cb !important; color: #155724; font-weight: bold; }
        .incorrecta { background-color: #f8d7da !important; border-color: #f5c6cb !important; color: #721c24; }
        
        .feedback-box { display: none; margin-top: 15px; padding: 15px; border-radius: 10px; border-left: 6px solid; font-size: 0.95em; }
        .fb-correcta { background: #e2fbe4; border-color: #2ecc71; color: #1e4620; }
        .fb-incorrecta { background: #fff0f0; border-color: #e74c3c; color: #6d1a1a; }

        /* Clases de resaltado */
        .hl-yellow { background-color: var(--p-amarillo); }
        .hl-blue { background-color: var(--p-azul); }
        .hl-purple { background-color: var(--p-morado); }
    </style>
</head>
<body>

<div class="card">
    <h1 style="text-align: center;">🕵️‍♂️ Misión Detective: Repaso Cuarto Básico</h1>
    
    <div class="toolbar">
        <button class="btn btn-purple" onclick="highlight('hl-purple')">🟣 Destacar Pregunta</button>
        <button class="btn btn-yellow" onclick="highlight('hl-yellow')">🟡 Marcar Pista (R)</button>
        <button class="btn btn-blue" onclick="highlight('hl-blue')">🔵 Marcar Causa</button>
        <button class="btn btn-clear" onclick="clearHighlight()">❌ Borrar</button>
    </div>

    <div class="texto-lectura">
        <h2 style="text-align: center;">Las tres mentiras</h2>
        <p>Ya en su lecho de muerte, un campesino llamó a sus tres hijos para entregarles en herencia <strong>“los ahorritos de toda su vida”</strong>. Les pidió que se los repartieran como “buenos hermanos”, pero los dos mayores, que eran igualmente ambiciosos, quisieron quedarse con todo.</p>
        <p>Para conseguirlo, propusieron al menor dejar la herencia enterrada y salir a rodar tierras durante un año. El dinero se entregaría al que contara la mentira más grande.</p>
        <p>Al final, el hermano menor dijo: —Subí a la luna a prender mi vela. ¿Por dónde bajé? ¡Por el garbanzo que tú plantaste!</p>
        <p>Los hermanos mayores le entregaron el dinero sin chistar al menor, que era el menos ambicioso.</p>
    </div>

    <hr>

    <div class="pregunta" id="q1">
        <p><strong>1. 🟣 Destaca la pregunta:</strong> ¿Qué herencia entregó el padre?</p>
        <div class="opcion" onclick="checkAnswer(this, 'incorrecta', 'r1', '¡Cuidado! El hilo aparece en las mentiras de los hermanos, pero no fue lo que el papá dejó al morir. Relee el primer párrafo.')">A) Un hilo largo y garbanzos.</div>
        <div class="opcion" onclick="checkAnswer(this, 'correcta', 'r1', '¡Excelente! Encontraste la información explícita. El padre dejó sus ahorros. ¿Lo destacaste en 🟡 amarillo?')">B) Los ahorritos de toda su vida.</div>
        <div id="r1" class="feedback-box"></div>
    </div>

    <div class="pregunta" id="q2">
        <p><strong>2. 🟣 Destaca la pregunta:</strong> ¿Por qué hicieron el concurso?</p>
        <div class="opcion" onclick="checkAnswer(this, 'correcta', 'r2', '¡Muy bien! La causa es la ambición de los hermanos mayores que querían todo el dinero para ellos.')">A) Por la ambición de los hermanos mayores.</div>
        <div class="opcion" onclick="checkAnswer(this, 'incorrecta', 'r2', 'No es correcto. Aunque el padre les pidió ser buenos hermanos, el concurso fue idea de los hijos para no compartir el dinero.')">B) Porque el padre se los pidió.</div>
        <div id="r2" class="feedback-box"></div>
    </div>

    <div class="pregunta">
        <p><strong>3. Pregunta de Opinión (2 ptos):</strong> ¿Crees que fue justo que ganara el menor?</p>
        <textarea id="opinion" rows="4" style="width: 100%; border-radius: 10px; border: 2px solid #ddd; padding: 10px;" placeholder="Escribe aquí tu respuesta siguiendo los 4 pasos..."></textarea>
        <button class="btn" style="margin-top:10px; background: #2ecc71; color: white;" onclick="document.getElementById('r3').style.display='block'">Enviar Respuesta</button>
        <div id="r3" class="feedback-box fb-correcta">
            <strong>Pauta de corrección:</strong><br>
            Para tener el puntaje completo revisa si: <br>
            1. Repetiste la pregunta. <br>
            2. Tomaste postura. <br>
            3. Usaste evidencia del texto (ej: el menor fue ingenioso). <br>
            4. Hiciste una reflexión final.
        </div>
    </div>

</div>

<script>
    function checkAnswer(element, status, feedbackId, message) {
        // Limpiar opciones anteriores en esa pregunta
        const parent = element.parentElement;
        const options = parent.querySelectorAll('.opcion');
        options.forEach(opt => opt.className = 'opcion');

        // Marcar la elegida
        element.classList.add(status);

        // Mostrar retroalimentación
        const fb = document.getElementById(feedbackId);
        fb.innerHTML = (status === 'correcta' ? '✅ ' : '❌ ') + message;
        fb.style.display = 'block';
        fb.className = 'feedback-box ' + (status === 'correcta' ? 'fb-correcta' : 'fb-incorrecta');
    }

    function highlight(className) {
        const sel = window.getSelection();
        if (!sel.rangeCount || sel.isCollapsed) return;
        const range = sel.getRangeAt(0);
        const span = document.createElement('span');
        span.className = className;
        range.surroundContents(span);
        sel.removeAllRanges();
    }

    function clearHighlight() {
        const sel = window.getSelection();
        if (!sel.rangeCount) return;
        const parent = sel.anchorNode.parentElement;
        if (parent.tagName === 'SPAN') {
            parent.replaceWith(...parent.childNodes);
        }
    }
</script>

</body>
</html>
