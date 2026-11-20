# Matrices paso a paso (JavaScript + PHP)

Aplicación web que resuelve sistemas de ecuaciones lineales (Gauss-Jordan) y calcula la matriz inversa, mostrando cada operación de fila.

## Cómo ejecutarla
Requiere PHP 8.0 o superior. En una terminal, dentro de esta carpeta:

    php -S localhost:8000
    ó
    php -S 127.0.0.1:8000

Luego abre http://localhost:8000 (o http://127.0.0.1:8000) en el navegador. (También funciona dentro de XAMPP/WAMP: copia la carpeta a `htdocs o www` y abre `http://localhost/sirm/`.)

## Estructura
- `index.html`, `css/styles.css`: interfaz con tablas dinámicas.
- `js/app.js`: interfaz, historial y `localStorage`.
- `php/api.php`: recibe la matriz (JSON), crea el objeto adecuado y devuelve pasos y resultado.
- `php/clases/`: clases PHP del cálculo.

## Programación orientada a objetos
| Concepto | PHP | JavaScript |
|---|---|---|
| Herencia | `SistemaLineal` y `MatrizInversa` extienden `MetodoMatricial` (comparten `gaussJordan()` y `registrar()`) | `ModuloSistema` y `ModuloInversa` extienden `Modulo` |
| Polimorfismo | `ejecutar()` y `nombre()` abstractos; `api.php` los llama sin saber qué clase es (interfaz `Ejecutable`) | `dimensiones()`, `mostrarResultado()`, `resumen()` redefinidos en cada módulo |
| Encapsulamiento | `Fraccion` con `private $n, $d`; `$pasos` privado en `MetodoMatricial` | `Almacen`, `Historial` y `ClientePhp` con campos privados `#` |
| Abstracción | `abstract class MetodoMatricial`, `interface Ejecutable` | Clase base `Modulo` |

## localStorage
Se guardan: el borrador de cada tabla, la pestaña activa y el historial de los últimos 15 cálculos (se pueden reabrir con un clic).

## Límites
Dimensiones de 1 a 8. Los cálculos usan fracciones exactas con enteros de PHP; con números muy grandes la app avisa en vez de redondear.
