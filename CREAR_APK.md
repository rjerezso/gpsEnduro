# 📱 Cómo Convertir Enduro Route a APK para Android

## Opción 1: PWABuilder (Más Fácil) ⭐ RECOMENDADO

### Pasos:

1. **Sube tu app a un hosting** (necesitas que esté online con HTTPS):
   - GitHub Pages (gratis)
   - Netlify (gratis)
   - Vercel (gratis)
   - O cualquier hosting

2. **Ve a [PWABuilder.com](https://www.pwabuilder.com/)**

3. **Pega la URL de tu app** y haz clic en "Start"

4. **Haz clic en "Package for stores"**

5. **Selecciona "Android"** → Descargar APK

6. **¡Listo!** Tendrás un archivo APK instalable

---

## Opción 2: Bubblewrap (Línea de comandos)

### Requisitos:
- Node.js instalado
- Android SDK (o Android Studio)

### Pasos:

```bash
# Instalar Bubblewrap
npm install -g @aspect-build/aspect-cli

# Inicializar proyecto
npx @aspect-build/aspect-cli init --manifest https://tu-url.com/manifest.json

# Generar APK
npx @aspect-build/aspect-cli build
```

---

## Opción 3: Capacitor (Para más control)

### Pasos:

```bash
# Crear carpeta del proyecto
mkdir enduro-app && cd enduro-app

# Inicializar npm
npm init -y

# Instalar Capacitor
npm install @capacitor/core @capacitor/cli @capacitor/android

# Inicializar Capacitor
npx cap init "Enduro Route" "com.enduro.gps"

# Crear carpeta www y copiar archivos
mkdir www
cp ../index.html www/
cp ../manifest.json www/
cp ../sw.js www/

# Añadir plataforma Android
npx cap add android

# Abrir en Android Studio
npx cap open android
```

Luego en Android Studio: Build → Build Bundle(s) / APK(s) → Build APK

---

## Opción 4: Apache Cordova

```bash
# Instalar Cordova
npm install -g cordova

# Crear proyecto
cordova create enduro-app com.enduro.gps EnduroRoute

cd enduro-app

# Copiar archivos a www/
cp ../index.html www/
cp ../manifest.json www/
cp ../sw.js www/

# Añadir plataforma Android
cordova platform add android

# Construir APK
cordova build android
```

El APK estará en: `platforms/android/app/build/outputs/apk/`

---

## 📋 Archivos necesarios para la APK:

```
📁 tu-proyecto/
├── index.html      ✅ (tu app principal)
├── manifest.json   ✅ (configuración PWA)
├── sw.js          ✅ (service worker)
└── icons/         (opcional - iconos PNG)
    ├── icon-192.png
    └── icon-512.png
```

---

## 🎨 Generar Iconos PNG (opcional pero recomendado)

Para iconos de alta calidad, crea imágenes PNG:
- **icon-192.png** (192x192 px)
- **icon-512.png** (512x512 px)

Puedes usar herramientas como:
- Canva.com
- Figma.com
- GIMP

---

## ⚡ Hosting Gratuito Rápido con GitHub Pages

1. Crea un repositorio en GitHub
2. Sube los 3 archivos (index.html, manifest.json, sw.js)
3. Ve a Settings → Pages
4. Selecciona "main" branch → Save
5. Tu URL será: `https://tu-usuario.github.io/tu-repo/`

---

## 🔧 Permisos Android necesarios

La app necesitará estos permisos (se añaden automáticamente):
- `ACCESS_FINE_LOCATION` - GPS preciso
- `ACCESS_COARSE_LOCATION` - Ubicación aproximada
- `INTERNET` - Para cargar mapas
- `WAKE_LOCK` - Mantener pantalla encendida

---

## ❓ Problemas comunes

### "Service Worker no registra"
- Necesitas HTTPS (localhost funciona para pruebas)

### "GPS no funciona en APK"
- Verifica permisos en Android Settings
- Asegúrate de usar HTTPS

### "Mapas no cargan offline"
- Los mapas requieren conexión
- Podrías implementar descarga de tiles para offline

---

## 🎉 ¡Listo!

Una vez tengas la APK, puedes:
1. Instalarla directamente en tu Android
2. Subirla a Google Play Store (requiere cuenta de desarrollador $25)
3. Compartirla por WhatsApp, email, etc.

**Nota:** Para instalar APK externas, activa "Orígenes desconocidos" en Android.
