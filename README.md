# Calculadora de Baremo - Catedráticos Andalucía 2026

Herramienta web interactiva diseñada para que el profesorado de Andalucía pueda **calcular de forma orientativa y sencilla** la puntuación de sus méritos para el concurso de acceso a Catedráticos (Orden de 18 de septiembre de 2026, BOJA n.º 183).

La aplicación traduce la complejidad del baremo oficial (10 puntos divididos en 3 bloques) a una interfaz visual, moderna e intuitiva.

## ✨ Características principales

* **Fidelidad total al BOJA:** Los cálculos respetan los topes exactos (5,5 ptos. para Trabajo desarrollado, 3,0 para Formación y 3,0 para Méritos académicos).
* **Gestión inteligente de la antigüedad (1.1):**
  * Calcula automáticamente el exceso sobre los 8 años mínimos exigidos.
  * Alerta en tiempo real si aún no cumples con el requisito de antigüedad (indicando los años que faltan y el año estimado en que podrás participar).
  * **Botón de "Estabilización":** Adaptado para quienes obtuvieron plaza sin realizar la fase de prácticas.
  * Validación de la relación de años entre prácticas y carrera (tolerancia de +1 o +2 años).
* **Sistema dinámico de Idiomas (3.1.10, 3.1.11):** 
  * Gestión coordinada de certificados de la Escuela Oficial de Idiomas (EOI) y ACLES.
  * Selección automática de la puntuación más alta por idioma, evitando duplicidades (solo cuenta el nivel superior).
* **Diseño UX/UI Avanzado:**
  * Modo claro y **modo oscuro** (se guarda la preferencia del usuario).
  * Barras de progreso por cada bloque que se iluminan al alcanzar el máximo.
  * Diseño totalmente *responsive* (adaptado a móviles, tablets y ordenadores).
* **Guardado automático:** Los datos se guardan en el navegador (`localStorage`), por lo que no perderás la información si recargas la página.
* **Sin dependencias:** Todo el código (HTML, CSS y JavaScript puro) está integrado en un solo archivo. No requiere instalación ni servidores.

## 🚀 ¿Cómo usarla?

No necesitas instalar nada. Solo tienes que:
1. Descargar el archivo `index.html` de este repositorio.
2. Hacer doble clic sobre él para abrirlo en tu navegador web.
*(O puedes visitar la versión desplegada a través de **GitHub Pages** si está activada).*

## ⚠️ Aviso Legal

**Esta herramienta es orientativa.** No es un servicio oficial ni está vinculada a la Junta de Andalucía. Los resultados son únicamente estimaciones basadas en la lectura del BOJA y **no sustituyen la baremación oficial** que realicen las comisiones de baremación. Las bases y criterios pueden variar o sufrir correcciones; verifica siempre la normativa vigente.

## 👨‍💻 Autoría

Calculadora creada a través de **DeepSeek** y **GitHub Copilot** por [fcallejah](https://github.com/fcallejah).
Si encuentras algún error o quieres proponer una mejora, ¡siéntete libre de abrir un *Issue* o un *Pull Request*!
