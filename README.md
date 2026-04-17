# IBNR Reserving — Mack & Bootstrap Chain-Ladder

Herramienta web actuarial para el cálculo de reservas técnicas IBNR mediante los métodos de *Mack (1993)* y *Bootstrap Chain-Ladder. Desarrollada como proyecto de la asignatura *Herramientas de Cálculo Actuarial de la Universidad Carlos III de Madrid.

> Traslado fiel del código VBA desarrollado en clase a un entorno web interactivo, sin dependencias de servidor.

---

## Funcionalidades

- *Método de Mack (1993):* reserva puntual, error estándar y distribución lognormal implícita por método de momentos.
- *Bootstrap Chain-Ladder:* distribución empírica completa de la reserva total con N simulaciones configurables (hasta 50.000).
- *KDE suavizado* (Silverman, 1986) superpuesto a la curva lognormal de Mack para comparación visual directa.
- *Detección automática de outliers* en factores empíricos mediante tres reglas combinadas (IQR Tukey, ratio de mediana excluyente, ratio par), con opciones de winsorización o eliminación.
- *Carga flexible de datos:* pegado directo, Excel/CSV/TXT, o imagen (extracción automática mediante la API de Claude).
- *Exportación* en CSV, Excel (.xlsx) y PDF ejecutivo, todo procesado en el cliente.

---

## Uso

La aplicación es un único archivo HTML autocontenido. No requiere instalación ni servidor.

1. Descarga IBNR.html.
2. Ábrelo en cualquier navegador moderno.
3. Carga tu triángulo de desarrollo acumulado (pegado, archivo o imagen).
4. Configura el número de simulaciones y pulsa *Proyectar*.

Los datos nunca abandonan tu equipo, salvo si usas la extracción por imagen (que llama a la API de Claude).

---

## Estructura del triángulo

La herramienta espera un triángulo de desarrollo *acumulado*:

- Una fila por año de accidente, el más antiguo arriba.
- Columnas = años de desarrollo.
- Separador: tabulación, coma o punto y coma. Se admite coma decimal europea.


13843232    33460360    37803985    39017070    39643535    39811678
15751359    31911270    35543132    36900361    37381751
13217414    25874275    28882421    29611783
 7147153    16173401    17998872
 7290008    16117555
 9722073


---

## Tecnologías

| Librería | Uso |
|---|---|
| [Chart.js 4.4](https://www.chartjs.org/) | Visualizaciones interactivas |
| [SheetJS](https://sheetjs.com/) | Lectura de archivos Excel |
| [jsPDF](https://github.com/parallax/jsPDF) | Generación de PDF en cliente |
| [Claude API](https://www.anthropic.com/) | Extracción de triángulos desde imagen (opcional) |

Todas las librerías se cargan desde CDN. No hay dependencias npm ni proceso de build.

---

## Base teórica

- Mack, T. (1993). Distribution-free calculation of the standard error of chain ladder reserve estimates. ASTIN Bulletin, 23(2), 213–225.
- Silverman, B.W. (1986). Density Estimation for Statistics and Data Analysis. Chapman & Hall.

---

## Autores

*Sol Formichelli · Javier Castillo*  
Universidad Carlos III de Madrid — Herramientas de Cálculo Actuarial
