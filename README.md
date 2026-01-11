# Blocklist Cibersaludables para uBlock Origin

Blocklist diseñada para **uBlock Origin** que permite **bloquear contenido específico relacionado con “Zona Gemelos”** en YouTube y redes sociales, utilizando **filtrado por URL y por DOM** a nivel de navegador.

Esta lista está pensada para **control parental, reducción de distracciones y curación de contenido**, y **NO** para firewalls ni filtros DNS.

---

## Objetivo

Bloquear de forma eficaz:

- Canales completos de YouTube
- Vídeos individuales por ID
- Resultados de búsqueda de YouTube por palabras clave
- Perfiles asociados en redes sociales (Instagram, Kick)
- Acceso directo mediante enlaces compartidos

Todo ello **sin bloquear YouTube por completo**.

---

## Navegadores de internet compatibles 

### ✔️ Compatible
- **Firefox + uBlock Origin (versión completa)**
- LibreWolf / Waterfox (basados en Firefox)

### ⚠️ Compatibilidad limitada
- Chrome / Edge / Brave  
  (solo `uBlock Origin Lite` → **NO recomendado**)

### ❌ NO compatible
- Firewalla / NextDNS / Pi-hole (DNS)
- iOS / Android (apps de YouTube)
- Safari
- Smart TVs (Samsung, LG, Android TV)

> Esta blocklist funciona **exclusivamente a nivel de navegador con la extensión uBlock origin instalada**, no a nivel de red ni de sistema operativo.

---

## Tipos de bloqueo incluidos

### 1️⃣ Bloqueo por URL directa
Ejemplos:
```
||youtube.com/watch?v=VIDEOID
||instagram.com/usuario
||kick.com
```

- Bloquea el acceso directo incluso si se pega la URL
- Eficaz contra enlaces compartidos

---

### 2️⃣ Bloqueo por canal (DOM-based)
Ejemplo:
```
youtube.com##ytd-video-renderer:has(a[href*="/channel/UCxxxx"])
```

- Oculta **todos los vídeos de un canal** en:
  - recomendaciones
  - listados
  - resultados de búsqueda
- Muy eficiente (1 regla → cientos de vídeos)

⚠️ Nota: este método depende de la estructura HTML de YouTube y puede requerir mantenimiento si YouTube cambia su interfaz.

---

### 3️⃣ Bloqueo de búsquedas por palabras clave vinculadas con zona gemelos (p.e: gala zona gemelos, la casa de los gemelos...)
Ejemplo:
```
||youtube.com/results?search_query=la+casa+de+los+gemelos
```

- Bloquea páginas de resultados de búsqueda concretas
- Coincidencia literal por URL (no semántica)

---

### 4 Bloqueo de los vídeos
Ejemplo:
```
||youtube.com/watch?v=J2NN9_7Atgo
```

- Bloquea todos los videos de youtube publicados desde los perfiles de zona gemelos (ver la fecha de actualización)

---

## 📁 Estructura recomendada del repositorio

```
.
├── README.md
└── cibersaludables-gemelos.txt
```

---

## 🚀 Cómo instalar la blocklist en uBlock Origin

1. Instala **uBlock Origin** en Firefox
2. Abre el panel de uBlock → ⚙️ *Dashboard*
3. Ve a **Filter lists**
4. En la sección **Custom**, añade la URL `raw` del archivo:
   ```
   https://raw.githubusercontent.com/cibersaludables/blocklist/main/cibersaludables-gemelos.txt
   ```
5. Pulsa **Apply changes**

uBlock Origin actualizará la lista automáticamente de forma periódica.

---

## ⚠️ Limitaciones conocidas

- ❌ No bloquea contenido en la **app de YouTube**
- ❌ No funciona en móviles iOS / Android
- ❌ No funciona en Smart TVs
- ❌ No es aplicable a firewalls o DNS
- ⚠️ Las reglas DOM pueden romperse si YouTube cambia su HTML

---

## 🔄 Mantenimiento y actualización

- Los vídeos individuales se extraen mediante `yt-dlp`
- Cuando un canal publica nuevos vídeos:
  1. Se regenera la lista
  2. Se actualiza el fichero
  3. Se hace commit
- uBlock Origin descarga automáticamente los cambios

---

## 📜 Licencia

MIT License.

---

## 📌 Nota final

Esta blocklist **no pretende censurar YouTube**, sino **permitir un control granular y consciente del contenido** en entornos familiares o educativos, respetando la privacidad del usuario y sin inspección del tráfico HTTPS.

---

*Última actualización: 2026-01-11*  
*Versión: 1.0.0*
