DOCUMENTACIÓN TÉCNICA
CALCULADORA CIENTÍFICA PROFESIONAL
Versión: 1.0
Fecha: Febrero 2026
Autor: Documentación para estudiantes y desarrolladores
Lenguajes: HTML5, CSS3, JavaScript ES6
________________________________________
ÍNDICE
1.	Descripción General
2.	Estructura del Proyecto
3.	Arquitectura HTML
4.	Sistema de Estilos CSS
5.	Lógica JavaScript
6.	Variables Globales
7.	Funciones Principales
8.	Responsive Design
9.	Guía de Mantenimiento
10.	Ejercicios de Ampliación
11.	Solución de Problemas
________________________________________
DESCRIPCIÓN GENERAL
Propósito del Proyecto
Esta calculadora científica web proporciona una interfaz completa para realizar operaciones matemáticas básicas y avanzadas directamente desde el navegador. Está diseñada para ser:
•	Educativa: Código completamente documentado para aprendizaje
•	Funcional: Todas las operaciones comunes de calculadoras científicas
•	Responsive: Adaptable a cualquier tamaño de pantalla
•	Profesional: Diseño moderno tipo calculadora física
Características Principales
Operaciones Básicas
•	Suma (+)
•	Resta (−)
•	Multiplicación (×)
•	División (÷)
•	Módulo (mod) - resto de división
Funciones Científicas
•	Trigonometría: sin, cos, tan (en radianes)
•	Logaritmos: log (base 10), ln (base e)
•	Raíz cuadrada (√)
•	Potencia al cuadrado (x²)
•	Inverso (1/x)
•	Porcentaje (%)
Funciones de Memoria
•	MC (Memory Clear): Limpia la memoria
•	MR (Memory Recall): Recupera el valor de memoria
•	M+ (Memory Add): Suma al valor en memoria
•	M- (Memory Subtract): Resta del valor en memoria
Constantes Matemáticas
•	π (Pi): 3.141592653589793
•	e (Euler): 2.718281828459045
Funcionalidades Adicionales
•	Cambio de signo (±)
•	Borrado total (AC)
•	Borrado del último dígito (Backspace)
•	Copiar resultado al portapapeles
•	Soporte completo de teclado
•	Notación científica automática
•	Contador de precisión decimal
________________________________________
ESTRUCTURA DEL PROYECTO
Organización del Código
El proyecto está contenido en un único archivo HTML que incluye:
calculadora-cientifica.html
├── <head>
│   ├── Metadatos (charset, viewport)
│   ├── Título de la página
│   ├── Enlace a Font Awesome (iconos)
│   └── <style> - Todo el CSS
└── <body>
    ├── Estructura HTML de la calculadora
    └── <script> - Todo el JavaScript
Ventajas de esta Estructura
✅ Ventajas:
•	Un solo archivo, fácil de compartir
•	No requiere servidor web (se abre directamente)
•	No hay dependencias locales (solo Font Awesome CDN)
•	Ideal para prototipado y aprendizaje
⚠️ Consideraciones:
•	En proyectos grandes, se recomienda separar CSS y JS en archivos externos
•	Para producción, considera minificar el código
Estructura Alternativa (Recomendada para Proyectos Grandes)
proyecto/
├── index.html (solo estructura)
├── css/
│   └── estilos.css
├── js/
│   └── calculadora.js
└── README.md
________________________________________
ARQUITECTURA HTML
Jerarquía de Elementos
<body>
  └── <div class="calculadora">          [Contenedor principal]
      ├── <div class="header">            [Título]
      ├── <div class="display-container"> [Pantalla]
      │   ├── <div class="display-operacion">  [Operación actual]
      │   └── <div class="display">            [Número/resultado]
      ├── <div class="memoria-display">   [Display de memoria]
      ├── <div class="info-panel">        [Información adicional]
      │   ├── <div class="info-item">     [Notación científica]
      │   └── <div class="info-item">     [Precisión]
      ├── <div class="botones-grid">      [Rejilla de botones]
      │   └── [40+ botones]
      ├── <div class="acciones-grid">     [Botones de acción]
      │   ├── Copiar
      │   └── Borrar
      └── <div class="brand">             [Marca]
Componentes Clave
1. Display Container (Pantalla)
<div class="display-container">
    <div class="display-operacion" id="displayOperacion">0</div>
    <div class="display" id="display">0</div>
</div>
Función:
•	display-operacion: Muestra la operación en curso (ej: "5 +")
•	display: Muestra el número actual o resultado
IDs importantes:
•	Permiten acceso desde JavaScript con getElementById()
•	Deben ser únicos en toda la página
2. Botones Grid (Rejilla de Botones)
<div class="botones-grid">
    <button class="btn btn-numero" onclick="agregarNumero('7')">7</button>
    <button class="btn btn-operacion" onclick="seleccionarOperacion('suma')">+</button>
    <button class="btn btn-funcion" onclick="aplicarFuncion('sin')">sin</button>
</div>
Clases aplicadas:
•	btn: Clase base (estilos comunes a todos los botones)
•	btn-numero: Botones numéricos (0-9, punto)
•	btn-operacion: Operaciones matemáticas (+, -, ×, ÷)
•	btn-funcion: Funciones científicas (sin, cos, √)
•	btn-memoria: Funciones de memoria (MC, MR, M+, M-)
Event Handlers (onclick):
•	Ejecutan funciones JavaScript al hacer clic
•	Pasan parámetros entre comillas: onclick="agregarNumero('7')"
________________________________________
SISTEMA DE ESTILOS CSS
Metodología de Diseño
Reset Global
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
¿Por qué?
•	Elimina estilos por defecto inconsistentes entre navegadores
•	box-sizing: border-box facilita el cálculo de tamaños
Paleta de Colores
/* Colores principales */
Fondo degradado: #1e3c72 → #2a5298 (azul oscuro a medio)
Contenedor: #2d3748 (gris oscuro)
Display: #1a202c (casi negro)
Texto display: #48bb78 (verde LED)
Error: #fc8181 (rojo claro)

/* Colores de botones */
Números: #4a5568 (gris medio)
Operaciones: #3182ce (azul)
Funciones: #805ad5 (morado)
Memoria: #d97706 (naranja)
Borrar: #e53e3e (rojo)
Igual: #48bb78 (verde)
Filosofía de color:
•	Verde para resultados (simula LED de calculadora clásica)
•	Azul para operaciones (neutro, profesional)
•	Naranja para memoria (destacado, especial)
•	Rojo para errores y borrado (advertencia)
Sistemas de Layout
1. Flexbox (Centrado Principal)
body {
    display: flex;
    justify-content: center;  /* Centra horizontalmente */
    align-items: center;      /* Centra verticalmente */
    min-height: 100vh;        /* Altura completa de viewport */
}
Uso: Centrar la calculadora en la pantalla
2. CSS Grid (Rejilla de Botones)
.botones-grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);  /* 5 columnas iguales */
    gap: 8px;  /* Espacio entre elementos */
}
Ventajas de Grid:
•	Organización automática en filas y columnas
•	Fácil de modificar (cambiar número de columnas)
•	Responsive por naturaleza
Botón que ocupa 2 columnas:
.btn-igual {
    grid-column: span 2;  /* Expande 2 columnas */
}
Efectos Visuales
1. Degradados (Gradients)
background: linear-gradient(135deg, #3182ce, #2c5aa0);
Parámetros:
•	135deg: Ángulo (diagonal de esquina a esquina)
•	Colores: Del primero al segundo
Tipos de degradados:
•	linear-gradient: Línea recta
•	radial-gradient: Circular (no usado en este proyecto)
2. Sombras
/* Sombra exterior (elevación) */
box-shadow: 0 4px 0 rgba(0, 0, 0, 0.3);

/* Sombra interior (profundidad) */
box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.5);

/* Brillo de texto */
text-shadow: 0 0 10px rgba(72, 187, 120, 0.3);
Anatomía de box-shadow:
box-shadow: offset-x offset-y blur spread color;
•	offset-x: Desplazamiento horizontal
•	offset-y: Desplazamiento vertical
•	blur: Difuminado
•	spread: Expansión
•	color: Color (usar rgba para transparencia)
3. Transiciones
transition: all 0.2s ease;
Propiedades:
•	all: Anima todos los cambios de propiedades
•	0.2s: Duración (200 milisegundos)
•	ease: Curva de animación
Tipos de curvas:
•	linear: Velocidad constante
•	ease: Lenta-rápida-lenta (por defecto)
•	ease-in: Comienza lento
•	ease-out: Termina lento
•	ease-in-out: Lenta al inicio y final
4. Transformaciones
/* Al hacer clic (efecto de presionar) */
.btn:active {
    transform: translateY(2px);  /* Mueve 2px hacia abajo */
}

/* Al hacer hover (efecto de escala) */
.btn-accion:active {
    transform: scale(0.98);  /* Reduce a 98% del tamaño */
}
________________________________________
LÓGICA JAVASCRIPT
Modelo de Datos
Estado de la Calculadora
La calculadora mantiene su estado en 6 variables globales:
let numeroActual = '0';        // String: número en pantalla
let operacionActual = null;     // String o null: 'suma', 'resta', etc.
let numeroAnterior = null;      // Number o null: primer operando
let reiniciarDisplay = false;   // Boolean: ¿reiniciar en próximo dígito?
let memoria = 0;                // Number: valor en memoria
let anguloEnRadianes = true;    // Boolean: modo de trigonometría
¿Por qué numeroActual es string?
•	Se construye carácter a carácter: "1" → "12" → "12.5"
•	Permite manejar el punto decimal fácilmente
•	Se convierte a número solo para cálculos
Flujo de Operaciones
1. Usuario ingresa: 5
   numeroActual = "5"

2. Usuario presiona: +
   operacionActual = "suma"
   numeroAnterior = 5
   reiniciarDisplay = true

3. Usuario ingresa: 3
   numeroActual = "3" (reemplaza el display)

4. Usuario presiona: =
   Ejecuta: 5 + 3 = 8
   numeroActual = "8"
   operacionActual = null
   numeroAnterior = null
Arquitectura de Funciones
Categorías Funcionales
FUNCIONES DE ENTRADA
├── agregarNumero(num)          - Añade dígitos
├── seleccionarOperacion(op)    - Selecciona operación
└── aplicarFuncion(funcion)     - Aplica función científica

FUNCIONES DE CÁLCULO
├── calcular()                  - Ejecuta operación básica
└── mostrarResultado(resultado) - Muestra y formatea resultado

FUNCIONES DE DISPLAY
├── actualizarDisplay()         - Refresca pantalla
└── actualizarMemoriaDisplay()  - Actualiza display de memoria

FUNCIONES DE UTILIDAD
├── limpiar()                   - AC (All Clear)
├── borrarUltimo()              - Backspace
├── cambiarSigno()              - +/- toggle
├── insertarPi()                - Inserta π
├── insertarE()                 - Inserta e
└── copiarResultado()           - Copia al portapapeles

FUNCIONES DE MEMORIA
├── memoriaLimpiar()            - MC
├── memoriaRecuperar()          - MR
├── memoriaSumar()              - M+
└── memoriaRestar()             - M-
________________________________________
VARIABLES GLOBALES
Tabla de Variables
Variable	Tipo	Valor Inicial	Propósito
numeroActual	String	'0'	Número mostrado en display
operacionActual	String/null	null	Operación seleccionada
numeroAnterior	Number/null	null	Primer operando
reiniciarDisplay	Boolean	false	Flag para reemplazar display
memoria	Number	0	Valor en memoria
anguloEnRadianes	Boolean	true	Modo trigonométrico
Referencias DOM
let display = document.getElementById('display');
let displayOperacion = document.getElementById('displayOperacion');
let infoPanel = document.getElementById('infoPanel');
let notacionCientifica = document.getElementById('notacionCientifica');
let precision = document.getElementById('precision');
let tooltip = document.getElementById('tooltip');
let memoriaDisplay = document.getElementById('memoriaDisplay');
¿Qué son referencias DOM?
•	DOM = Document Object Model (estructura de la página)
•	getElementById() busca elementos HTML por su ID
•	Guarda la referencia en una variable para acceso rápido
________________________________________
FUNCIONES PRINCIPALES
1. agregarNumero(num)
Propósito: Añade un dígito o punto decimal al display
Parámetros:
•	num (String): Dígito a añadir ('0'-'9' o '.')
Lógica:
function agregarNumero(num) {
    if (reiniciarDisplay) {
        // Si se presionó una operación, reemplaza el display
        numeroActual = num;
        reiniciarDisplay = false;
    } else {
        if (numeroActual === '0' && num !== '.') {
            // Reemplaza el 0 inicial (excepto si es punto decimal)
            numeroActual = num;
        } else if (num === '.' && numeroActual.includes('.')) {
            // Evita múltiples puntos decimales
            return;
        } else {
            // Concatena el dígito
            numeroActual += num;
        }
    }
    actualizarDisplay();
}
Casos especiales:
•	Si numeroActual = "0" y se presiona "5", resultado: "5" (no "05")
•	Si numeroActual = "3.14" y se presiona ".", no hace nada (ya hay punto)
•	Si se acaba de calcular un resultado, reemplaza con el nuevo número
2. seleccionarOperacion(operacion)
Propósito: Guarda la operación seleccionada (+, -, ×, ÷)
Parámetros:
•	operacion (String): 'suma', 'resta', 'multiplicacion', 'division', 'mod'
Lógica:
function seleccionarOperacion(operacion) {
    // Si hay una operación pendiente, la calcula primero
    if (numeroAnterior !== null && !reiniciarDisplay) {
        calcular();
    }
    
    operacionActual = operacion;
    numeroAnterior = parseFloat(numeroActual);
    reiniciarDisplay = true;
}
Comportamiento encadenado:
5 + 3 + 2 = ?

Paso 1: 5 → numeroActual = "5"
Paso 2: + → numeroAnterior = 5, operacionActual = "suma"
Paso 3: 3 → numeroActual = "3"
Paso 4: + → Calcula 5+3=8, luego numeroAnterior = 8
Paso 5: 2 → numeroActual = "2"
Paso 6: = → Calcula 8+2=10
3. calcular()
Propósito: Ejecuta la operación matemática pendiente
Sin parámetros (usa variables globales)
Lógica:
function calcular() {
    if (operacionActual === null || numeroAnterior === null) {
        return;  // No hay operación pendiente
    }

    const num1 = numeroAnterior;
    const num2 = parseFloat(numeroActual);
    let resultado;

    switch(operacionActual) {
        case 'suma':
            resultado = num1 + num2;
            break;
        case 'resta':
            resultado = num1 - num2;
            break;
        // ... otros casos
    }

    mostrarResultado(resultado);
    operacionActual = null;
    numeroAnterior = null;
    reiniciarDisplay = true;
}
Manejo de errores:
•	División por cero: Muestra mensaje de error
•	Raíz de número negativo: Muestra error
•	Logaritmo de número ≤ 0: Muestra error
4. aplicarFuncion(funcion)
Propósito: Aplica funciones científicas (sin, cos, √, etc.)
Parámetros:
•	funcion (String): 'sin', 'cos', 'tan', 'log', 'ln', 'raiz', 'potencia', 'porcentaje', 'inverso'
Ejemplo - Seno:
case 'sin':
    resultado = anguloEnRadianes 
        ? Math.sin(num) 
        : Math.sin(num * Math.PI / 180);
    displayOperacion.textContent = `sin(${num})`;
    break;
Operador ternario:
condicion ? valorSiTrue : valorSiFalse
Conversión de grados a radianes:
radianes = grados × π / 180
5. mostrarResultado(resultado)
Propósito: Muestra el resultado y actualiza información adicional
Parámetros:
•	resultado (Number): Resultado numérico
Lógica:
function mostrarResultado(resultado) {
    // Redondea a 12 decimales (evita errores de punto flotante)
    resultado = Math.round(resultado * 1000000000000) / 1000000000000;
    
    numeroActual = resultado.toString();
    actualizarDisplay();

    // Muestra información adicional
    infoPanel.style.display = 'grid';
    notacionCientifica.textContent = resultado.toExponential(4);
    
    const decimales = resultado.toString().split('.')[1];
    precision.textContent = decimales 
        ? decimales.length + ' dígitos' 
        : '0 dígitos';
}
¿Por qué redondear? JavaScript tiene problemas con decimales:
0.1 + 0.2 = 0.30000000000000004  // ❌ Error de punto flotante
El redondeo elimina estos errores.
6. copiarResultado() - Async Function
Propósito: Copia el resultado al portapapeles del sistema
Función asíncrona:
async function copiarResultado() {
    if (numeroActual === '0') return;

    try {
        await navigator.clipboard.writeText(numeroActual);
        tooltip.classList.add('show');
        setTimeout(() => tooltip.classList.remove('show'), 2000);
    } catch (err) {
        console.error('Error al copiar:', err);
    }
}
Conceptos clave:
•	async: Marca la función como asíncrona
•	await: Espera a que se complete la operación
•	try-catch: Maneja posibles errores (ej: permisos denegados)
•	setTimeout: Ejecuta código después de un delay
API del Portapapeles:
•	navigator.clipboard.writeText(): Requiere permisos del usuario
•	Solo funciona en HTTPS (o localhost)
________________________________________
RESPONSIVE DESIGN
Estrategia Mobile-First
El diseño se adapta a 3 rangos de pantalla:
1. Desktop (> 480px)
/* Estilos por defecto */
.calculadora { max-width: 420px; }
.display { font-size: 42px; }
.btn { padding: 16px 8px; font-size: 16px; }
2. Mobile (≤ 480px)
@media (max-width: 480px) {
    .calculadora { padding: 20px; }
    .display { font-size: 36px; }
    .btn { padding: 14px 6px; font-size: 14px; }
    .botones-grid { gap: 6px; }
}
3. Small Mobile (≤ 360px)
@media (max-width: 360px) {
    .display { font-size: 28px; }
    .btn { padding: 12px 4px; font-size: 12px; }
    .botones-grid { gap: 5px; }
}
Breakpoints Comunes
Dispositivo	Ancho típico	Breakpoint usado
iPhone SE	320px	≤ 360px
iPhone 12/13	390px	≤ 480px
iPhone 12/13 Pro Max	428px	≤ 480px
iPad Mini	768px	Desktop
Desktop	1024px+	Desktop
Técnicas Responsive Clave
1. Viewport Units
min-height: 100vh;  /* 100% de la altura visible */
•	vh = Viewport Height (1vh = 1% de altura)
•	vw = Viewport Width (1vw = 1% de ancho)
2. Flexbox Responsive
body {
    display: flex;
    justify-content: center;
    align-items: center;
}
Centra automáticamente en cualquier tamaño.
3. Grid Flexible
grid-template-columns: repeat(5, 1fr);
1fr se ajusta proporcionalmente al espacio disponible.
4. Max-width + Width
width: 100%;
max-width: 420px;
•	En desktop: 420px fijo
•	En mobile: 100% del ancho disponible
________________________________________
GUÍA DE MANTENIMIENTO
Modificar Colores
Cambiar el color principal:
1.	Busca en CSS: #3182ce (azul actual)
2.	Reemplaza con tu color (ej: #10b981 para verde)
3.	Verifica contraste de texto (usar herramienta online)
Cambiar fondo:
body {
    background: linear-gradient(135deg, TU_COLOR_1, TU_COLOR_2);
}
Añadir Nuevo Botón
1. HTML - Añadir botón:
<button class="btn btn-funcion" onclick="aplicarFuncion('nuevaFuncion')">
    Texto
</button>
2. JavaScript - Añadir lógica:
function aplicarFuncion(funcion) {
    // ... código existente
    
    case 'nuevaFuncion':
        resultado = /* tu cálculo */;
        displayOperacion.textContent = `tu_texto(${num})`;
        break;
}
Cambiar Número de Columnas
Para 4 columnas en lugar de 5:
.botones-grid {
    grid-template-columns: repeat(4, 1fr);  /* Cambiar 5 a 4 */
}
Reorganizar botones:
•	Los botones se colocan automáticamente de izquierda a derecha
•	Para saltar espacios: usar grid-column: span 1
Añadir Sonidos
1. Añadir archivo de audio:
<audio id="sonidoClick" src="click.mp3" preload="auto"></audio>
2. Reproducir en JavaScript:
function agregarNumero(num) {
    document.getElementById('sonidoClick').play();
    // ... resto del código
}
Guardar Estado (LocalStorage)
Guardar al calcular:
function mostrarResultado(resultado) {
    // ... código existente
    localStorage.setItem('ultimoResultado', resultado);
}
Recuperar al cargar:
window.addEventListener('load', () => {
    const ultimoResultado = localStorage.getItem('ultimoResultado');
    if (ultimoResultado) {
        numeroActual = ultimoResultado;
        actualizarDisplay();
    }
});
________________________________________
EJERCICIOS DE AMPLIACIÓN
Nivel Básico
1. Añadir Botón de Cambio de Tema
Objetivo: Alternar entre modo claro y oscuro
Pasos:
1.	Añadir botón en HTML
2.	Crear clase .tema-claro en CSS con colores invertidos
3.	JavaScript: document.body.classList.toggle('tema-claro')
2. Historial de Operaciones
Objetivo: Mostrar últimas 5 operaciones
Estructura:
let historial = [];

function agregarAlHistorial(operacion, resultado) {
    historial.unshift({ operacion, resultado });
    if (historial.length > 5) historial.pop();
    actualizarHistorial();
}
3. Modo Grados/Radianes
Objetivo: Botón para alternar entre RAD y DEG
Lógica:
let anguloEnRadianes = true;

function toggleRadianes() {
    anguloEnRadianes = !anguloEnRadianes;
    // Actualizar texto del botón
}
Nivel Intermedio
4. Funciones Trigonométricas Inversas
Funciones a implementar: arcsin, arccos, arctan
Código de ejemplo:
case 'arcsin':
    if (num < -1 || num > 1) {
        display.textContent = 'Error: arcsin(-1 ≤ x ≤ 1)';
        return;
    }
    resultado = Math.asin(num);
    break;
5. Potencia Genérica (x^y)
Objetivo: Permitir elevar a cualquier potencia
Modificar: Convertir operación a dos operandos
case 'potencia':
    resultado = Math.pow(num1, num2);
    break;
6. Factorial (n!)
Objetivo: Calcular factorial de números enteros
Algoritmo:
function factorial(n) {
    if (n < 0) return NaN;
    if (n === 0 || n === 1) return 1;
    return n * factorial(n - 1);
}
Nivel Avanzado
7. Conversión de Bases
Objetivo: Binario, Octal, Decimal, Hexadecimal
Funciones de JavaScript:
// Decimal a binario
num.toString(2)

// Binario a decimal
parseInt(binary, 2)

// Decimal a hexadecimal
num.toString(16)
8. Gráficos de Funciones
Objetivo: Graficar funciones matemáticas
Librería recomendada: Chart.js o Plotly.js
Ejemplo básico:
<canvas id="grafico"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
// Crear gráfico de sin(x)
const ctx = document.getElementById('grafico');
new Chart(ctx, {
    type: 'line',
    data: { /* datos */ }
});
</script>
9. Calculadora de Matrices
Objetivo: Operaciones con matrices (suma, multiplicación)
Estructura de datos:
const matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
10. Modo Programador
Objetivo: AND, OR, XOR, NOT, shifts binarios
Operadores en JavaScript:
num1 & num2   // AND
num1 | num2   // OR
num1 ^ num2   // XOR
~num          // NOT
num << 2      // Shift left
num >> 2      // Shift right
________________________________________
SOLUCIÓN DE PROBLEMAS
Problemas Comunes
1. Los botones no funcionan
Síntomas: Al hacer clic, no pasa nada
Causas posibles:
•	Error de sintaxis en JavaScript (revisar consola: F12)
•	Función no definida (verificar nombre exacto)
•	onclick mal escrito
Solución:
// En la consola del navegador (F12 → Console)
console.log(typeof agregarNumero);  // Debe mostrar "function"
2. Display no se actualiza
Síntomas: El número no cambia en pantalla
Causas posibles:
•	getElementById() no encuentra el elemento (ID incorrecto)
•	JavaScript cargando antes que HTML
Solución:
// Verificar que el elemento existe
console.log(display);  // No debe ser null

// Asegurar que JS se ejecuta después del HTML
document.addEventListener('DOMContentLoaded', function() {
    // Tu código aquí
});
3. Resultados incorrectos en decimales
Síntomas: 0.1 + 0.2 = 0.30000000000000004
Causa: Error de punto flotante de JavaScript
Solución: Redondear resultados
resultado = Math.round(resultado * 1e12) / 1e12;
4. Botones se ven mal en móvil
Síntomas: Botones muy pequeños o muy grandes
Causas posibles:
•	Falta la etiqueta viewport
•	Media queries no aplicadas
Solución:
<!-- En <head> -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
5. No se puede copiar al portapapeles
Síntomas: Error al presionar "Copiar"
Causas posibles:
•	Página no está en HTTPS (excepto localhost)
•	Permisos denegados por el usuario
Solución:
// Fallback para navegadores sin API de clipboard
function copiarResultado() {
    try {
        await navigator.clipboard.writeText(numeroActual);
    } catch (err) {
        // Método antiguo (fallback)
        const input = document.createElement('input');
        input.value = numeroActual;
        document.body.appendChild(input);
        input.select();
        document.execCommand('copy');
        document.body.removeChild(input);
    }
}
Depuración (Debugging)
Herramientas del Navegador
Abrir DevTools:
•	Chrome/Edge: F12 o Ctrl+Shift+I
•	Firefox: F12 o Ctrl+Shift+K
•	Safari: Cmd+Option+I
Consola (Console):
console.log(numeroActual);           // Mostrar valor
console.error('Error crítico');      // Mostrar error
console.table({ num1, num2, resultado }); // Tabla de datos
Breakpoints:
1.	Ir a "Sources" (Chrome) o "Debugger" (Firefox)
2.	Buscar el archivo HTML
3.	Hacer clic en el número de línea para añadir breakpoint
4.	Ejecutar el código, se pausará en el breakpoint
Inspeccionar elementos:
1.	Click derecho en elemento → "Inspeccionar"
2.	Ver estilos aplicados en "Styles"
3.	Modificar CSS en tiempo real para probar
Validación de Código
HTML Validator
Herramienta: https://validator.w3.org/
Errores comunes:
•	Etiquetas sin cerrar: <div>texto ❌ → <div>texto</div> ✅
•	Atributos duplicados
•	IDs duplicados
CSS Validator
Herramienta: https://jigsaw.w3.org/css-validator/
Errores comunes:
•	Propiedades inexistentes
•	Valores inválidos: margin: big; ❌
JavaScript Linter
Herramienta: ESLint (https://eslint.org/)
Configurar en VSCode:
1.	Instalar extensión "ESLint"
2.	Crea archivo .eslintrc.json
3.	Marca errores automáticamente
________________________________________
GLOSARIO DE TÉRMINOS
HTML
•	Tag (Etiqueta): <div>, <button>, etc.
•	Atributo: Propiedad de una etiqueta (id="nombre")
•	ID: Identificador único de un elemento
•	Clase: Identificador reutilizable (puede repetirse)
CSS
•	Selector: Define a qué elementos se aplican los estilos
•	Propiedad: Característica a modificar (color, font-size)
•	Valor: Dato asignado a una propiedad (red, 16px)
•	Pseudo-clase: Estado especial (:hover, :active)
JavaScript
•	Variable: Contenedor de datos (let, const)
•	Función: Bloque de código reutilizable
•	Parámetro: Valor que recibe una función
•	Return: Valor que devuelve una función
•	Event: Acción del usuario (click, keypress)
Matemáticas
•	Módulo (mod): Resto de una división
•	Logaritmo (log): Operación inversa de exponenciación
•	Radián: Unidad de medida angular (2π rad = 360°)
________________________________________
RECURSOS ADICIONALES
Documentación Oficial
HTML:
•	MDN Web Docs: https://developer.mozilla.org/es/docs/Web/HTML
CSS:
•	MDN Web Docs: https://developer.mozilla.org/es/docs/Web/CSS
•	CSS Tricks: https://css-tricks.com/
JavaScript:
•	MDN Web Docs: https://developer.mozilla.org/es/docs/Web/JavaScript
•	JavaScript.info: https://javascript.info/
Herramientas Útiles
Editores de código:
•	Visual Studio Code (recomendado)
•	Sublime Text
•	Atom
Navegadores para desarrollo:
•	Google Chrome (DevTools excelentes)
•	Firefox Developer Edition
•	Microsoft Edge (basado en Chromium)
Generadores de colores:
•	Coolors.co
•	Adobe Color
•	Paletton
Iconos:
•	Font Awesome: https://fontawesome.com/
•	Material Icons: https://fonts.google.com/icons
•	Feather Icons: https://feathericons.com/
Comunidades y Ayuda
Foros:
•	Stack Overflow (inglés)
•	Stack Overflow en Español
Discord/Slack:
•	FreeCodeCamp
•	The Programmer's Hangout
Tutoriales:
•	FreeCodeCamp.org
•	Codecademy
•	MDN Learn
________________________________________
CONTROL DE VERSIONES
Versión 1.0 (Actual)
Fecha: Febrero 2026
Características:
•	Operaciones básicas completas
•	Funciones científicas (trigonometría, logaritmos)
•	Sistema de memoria (MC, MR, M+, M-)
•	Constantes π y e
•	Responsive design
•	Soporte de teclado
•	Copiar al portapapeles
Próximas Versiones (Roadmap)
Versión 1.1:
•	Modo grados/radianes toggle
•	Historial de operaciones
•	Tema claro/oscuro
Versión 1.2:
•	Funciones trigonométricas inversas
•	Potencia genérica (x^y)
•	Factorial
Versión 2.0:
•	Conversión de bases
•	Modo programador (operaciones binarias)
•	Gráficos de funciones
________________________________________
LICENCIA Y CRÉDITOS
Tipo de proyecto: Educativo y Open Source
Uso permitido:
•	Uso personal y educativo ✅
•	Modificación y ampliación ✅
•	Uso comercial ✅
•	Redistribución ✅
Créditos:
•	Font Awesome para iconos
•	Inspiración en calculadoras científicas clásicas (Casio, HP)
Contribuciones: Si mejoras este código, considera compartir tus mejoras con la comunidad.
________________________________________
CONTACTO Y SOPORTE
Para preguntas o reportar errores:
•	Abrir un issue en el repositorio
•	Contactar al autor
•	Buscar en Stack Overflow
Antes de reportar un error:
1.	Verificar la consola del navegador (F12)
2.	Comprobar que el código está completo
3.	Probar en otro navegador
4.	Revisar esta documentación
________________________________________
FIN DE LA DOCUMENTACIÓN
Última actualización: Febrero 2026
Versión del documento: 1.0


