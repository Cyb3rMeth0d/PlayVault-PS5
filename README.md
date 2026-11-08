<div align="center">

# 🎮 PlayVault-PS5

### *Unified Multi-Gen Retro Hub & Launcher for PlayStation 5 Homebrew*
**Desarrollado con pasión por [Cyb3rMeth0d](https://github.com/Cyb3rMeth0d)**

---

[![PS5 Homebrew](https://img.shields.io/badge/Platform-PS5%20Homebrew-0070D1?style=for-the-badge&logo=playstation&logoColor=white)](#)
[![Systems Supported](https://img.shields.io/badge/Supported-PS1%20%E2%80%A2%20PS2%20%E2%80%A2%20PSP-00C853?style=for-the-badge)](#)
[![Build Status](https://img.shields.io/badge/Build-Release%20v1.0.0-FF9100?style=for-the-badge&logo=githubactions&logoColor=white)](#)
[![Community Discord](https://img.shields.io/badge/Discord-Join%20Community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](#)

<br/>

<p align="center">
  <b>PlayVault</b> transforma tu PS5 en un centro de emulación retro limpio, rápido e intuitivo.<br/>
  Indexa tu catálogo de <b>PlayStation 1, PlayStation 2 y PSP</b> de forma automática con carátulas dobles, alertas en tiempo real y arranque nativo directo sin configuraciones molestas de emuladores.
</p>

[✨ Características](#-características) • [🎥 Demostración](#-demostración-en-vídeo) • [🎮 Controles](#-controles-en-la-interfaz) • [📂 Rutas](#-rutas-y-almacenamiento) • [🖼️ Guía de Carátulas](#-guía-paso-a-paso-carátulas-dobles) • [⚙️ BIOS](#️-requisito-de-bios-ps2) • [🚀 Instalación](#-instalación)

---

### 🎥 Demostración en vídeo

https://github.com/user-attachments/assets/TU-ID-DE-VIDEO.mp4

---

</div>

## ✨ Características

* 🕹️ **Ecosistema PlayStation Unificado:** Acceso centralizado para títulos de PS1, PS2 y PSP en una interfaz fluida con ambientación estética y limpia.
* ⚡ **Plug & Play Automático:** Conecta tu USB (`/mnt/usb0/`) o guarda tus juegos en el almacenamiento interno (`/data/`); PlayVault detecta y clasifica todo al instante.
* 🖼️ **Presentación con Doble Carátula:** Muestra la portada principal (`cover.png`) y la contraportada trasera (`[Nombre]_back.png`) con selector dinámico.
* 🛡️ **Sensor Inteligente de BIOS:** El sistema analiza activamente los volcados de BIOS de PS2 e informa visualmente si falta algún archivo antes de ejecutar el juego[cite: 1].
* 🔎 **Búsqueda Instantánea & Filtrado:** Salta rápidamente entre plataformas con los botones superiores o encuentra cualquier juego al escribir con el botón de búsqueda[cite: 1].

---

## 🎮 Controles en la interfaz

Configuración nativa adaptada al DualSense:

| Botón | Función en PlayVault |
| :---: | :--- |
| <kbd>R1</kbd> / <kbd>R2</kbd> | Alternar entre categorías (`PS1` ➔ `PS2` ➔ `PSP`)[cite: 1] |
| <kbd>✖</kbd> | Iniciar juego seleccionado[cite: 1] |
| <kbd>■</kbd> | Abrir panel de ajustes[cite: 1] |
| <kbd>▲</kbd> | Activar barra de búsqueda[cite: 1] |
| <kbd>Touchpad</kbd> | Modo Explorador de archivos[cite: 1] |

---

## 📂 Rutas y almacenamiento

> 💡 **Formato recomendado para USB:** **exFAT** (recomendado para juegos pesados de PS2) o **FAT32** con partición **MBR**.

PlayVault rastrea de forma autónoma la raíz de tu unidad USB (`/mnt/usb0/`) o del disco interno (`/data/`)[cite: 1]:

```plaintext
/mnt/usb0/ (o /data/)
├── PSP/
│   └── GAME/              <-- Coloca aquí las carpetas de juegos de PSP
├── ps1/
│   └── games/             <-- Coloca aquí las carpetas de juegos de PS1
└── PCSX2/
    ├── bios/              <-- Archivo BIOS para PS2 (OBLIGATORIO)
    └── games/             <-- Coloca aquí las carpetas de juegos de PS2

---

## 🖼️ Guía completa: Sistema de carátulas dobles (Frontal y Trasera)

PlayVault cuenta con un visor dual que permite mostrar tanto la **portada frontal** como la **contraportada trasera** original de tus juegos. Para que el motor reconozca e indexe las imágenes sin errores gráficos, sigue estrictamente estas directrices:

---

## 1️⃣ Regla fundamental: 1 Juego = 1 Carpeta individual
**Nunca coloques archivos de juegos sueltos** directamente en la raíz de `games/` ni de `GAME/`.  
Cada juego debe estar aislado dentro de su propia subcarpeta dedicada. Dentro de esa misma carpeta convivirán el archivo del juego y sus dos imágenes correspondientes.

---

## 2️⃣ Esquema estricto de nombrado de archivos

| Tipo de carátula | Nombre obligatorio del archivo | Extensiones admitidas | Regla de coincidencia |
| :--- | :---: | :---: | :--- |
| **Carátula Frontal** *(Cover)* | `cover` | `.png` o `.jpg` | **Universal y fijo.** Siempre debe llamarse exactamente `cover.png` o `cover.jpg` en todos los juegos. |
| **Contraportada Trasera** *(Back)* | `[NombreExactoDelJuego]_back` | `.png` o `.jpg` | **Debe llevar el nombre completo e idéntico del archivo del juego** instalado (respetando espacios, mayúsculas y minúsculas), seguido del sufijo `_back`. |

> 📌 **Recomendación de formato:** Aunque se admite formato `.jpg`, **se recomienda rotundamente utilizar `.png`** para asegurar bordes limpios, soporte de transparencias y la mejor calidad posible en televisores 4K.

---

### 3️⃣ Ejemplos prácticos paso a paso

#### 🔹 Bloque 1: Consolas de sobremesa (PS1 y PS2)

* **PlayStation 1 (`.bin/.cue`)** ➔ Archivo: `Crash Bandicoot.bin`
* **PlayStation 2 (`.iso`)** ➔ Archivo: `DragonBall Z Budokai Tenkaichi 3.iso`

```plaintext
/mnt/usb0/
├── ps1/games/
│   └── Crash Bandicoot/
│       ├── Crash Bandicoot.bin
│       ├── Crash Bandicoot.cue
│       ├── cover.png                     <-- Frontal fija
│       └── Crash Bandicoot_back.png      <-- Trasera (mismo nombre que .bin)
│
└── PCSX2/games/
    └── DBZ Budokai Tenkaichi 3/
        ├── DragonBall Z Budokai Tenkaichi 3.iso
        ├── cover.png                     <-- Frontal fija
        └── DragonBall Z Budokai Tenkaichi 3_back.png <-- Trasera (mismo nombre que .iso)
/mnt/usb0/PSP/GAME/
└── GOW Ghost of Sparta/
    ├── God of War Ghost of Sparta.cso
    ├── cover.png                         <-- Frontal fija
    └── God of War Ghost of Sparta_back.png <-- Trasera (mismo nombre que .cso)
