# 🍳 MiMenú — Organizador de Comidas

> Planificá tu semana en la cocina, controlá tu despensa y generá tu lista de compras, todo desde el navegador. Sin instalaciones, sin cuenta, sin internet obligatorio.

---

## 📋 Índice

- [Descripción](#descripción)
- [Características](#características)
- [Capturas de pantalla](#capturas-de-pantalla)
- [Tecnologías utilizadas](#tecnologías-utilizadas)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Cómo usar la aplicación](#cómo-usar-la-aplicación)
  - [Planificador semanal](#planificador-semanal)
  - [Inventario](#inventario)
  - [Recetas](#recetas)
  - [Lista de compras](#lista-de-compras)
  - [Opciones](#opciones)
- [Datos y almacenamiento](#datos-y-almacenamiento)
- [Instalación como app (PWA)](#instalación-como-app-pwa)
- [Despliegue en GitHub Pages](#despliegue-en-github-pages)
- [Paleta de colores](#paleta-de-colores)
- [Roadmap](#roadmap)

---

## Descripción

**MiMenú** es una aplicación web progresiva (PWA) de una sola página (`index.html`) pensada para facilitar la organización de las comidas del hogar. Está orientada a todas las edades y funciona desde cualquier dispositivo con navegador, incluyendo celulares, tablets y computadoras.

Todo el contenido se guarda **localmente en el dispositivo** mediante `localStorage`, sin necesidad de servidores externos, cuentas de usuario ni conexión a internet después de la primera carga.

---

## Características

### 📅 Planificador semanal
- Vista de **3 semanas**: semana pasada, semana actual y próxima semana
- Organización por días (Lunes a Domingo) y por comida (Desayuno, Almuerzo, Merienda, Cena)
- Asignación de recetas guardadas a cada slot con un toque
- Marcar platos como ✅ **cocinados** o ⭕ pendientes
- Ver la receta completa directamente desde el slot
- **Copiar semana** al siguiente período
- **Limpiar semana** completa con un botón

### 📦 Inventario
- Lista precargada con **38 ingredientes comunes** listos para usar (aceites, harinas, carnes, verduras, lácteos, etc.)
- Botones **−** y **+** para ajustar cantidad de a 1 directamente, sin abrir formularios
- Soporte de unidades: **unidades (u)**, **kilogramos (kg)**, **litros (L)**, **gramos (g)**, **mililitros (ml)**
- **Fracción adicional** disponible para kg, L y unidades: indicá si además de la parte entera tenés ¼, ½ o ¾ más
- Filtro por **categoría** (Aceites y grasas, Carnes, Lácteos, Verduras, etc.)
- Buscador en tiempo real
- Alerta visual cuando un producto solo tiene fracción disponible (sin parte entera)
- Posibilidad de **agregar productos nuevos** con nombre, categoría, cantidad y unidad propias
- Los productos personalizados pueden eliminarse; los precargados siempre permanecen

### 📖 Recetas
- Crear recetas con nombre, lista de ingredientes y pasos de preparación
- Los ingredientes se eligen de la **lista maestra** (alfabética), con posibilidad de agregar uno nuevo al instante
- Para cada ingrediente se especifica: **cantidad numérica + unidad + fracción** (ej: `2 kg ½ Harina 0000`)
- Buscador de recetas
- Ver receta completa en modal con ingredientes y pasos numerados
- Editar o eliminar cualquier receta

### 🛒 Lista de compras
- Generación **automática** comparando los ingredientes del menú semanal contra el inventario disponible
- Solo aparecen los productos que realmente faltan, con la cantidad exacta necesaria
- Marcar ítems como comprados con checkbox
- Barra de **progreso visual** de la compra
- Agregar ítems **manualmente** (para cosas fuera de recetas)
- **Exportar** la lista pendiente como archivo `.txt` para imprimir o compartir

### ⚙️ Opciones
- **Modo oscuro / claro**
- **Tamaño de texto**: Normal, Grande, Muy grande (accesibilidad para adultos mayores)
- **Exportar datos** completos como archivo JSON (backup)
- **Importar datos** desde un JSON previamente exportado
- Borrar todos los datos (con confirmación)

---

## Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| HTML5 | Estructura y semántica |
| CSS3 | Estilos, variables de tema, diseño responsive |
| JavaScript (ES6+) | Lógica de la aplicación, estado, persistencia |
| LocalStorage | Almacenamiento de datos en el dispositivo |
| Google Fonts | Tipografías: *Fraunces* (display) y *DM Sans* (cuerpo) |

No se utilizan frameworks ni librerías externas de JavaScript. El proyecto es completamente **vanilla**.

---

## Estructura del proyecto

```
mimenu/
│
├── index.html       # Aplicación completa (HTML + CSS + JS en un solo archivo)
├── manifest.json    # Configuración PWA (nombre, íconos, tema)
├── sw.js            # Service Worker para funcionamiento offline
├── icon-192.png     # Ícono para instalación en Android
├── icon-512.png     # Ícono para splash screen
└── README.md        # Este archivo
```

> El archivo principal `index.html` contiene todo el CSS y JavaScript inline, lo que permite abrirlo directamente en el navegador sin ningún servidor.

---

## Cómo usar la aplicación

### Planificador semanal

1. Al abrir la app, se muestra automáticamente la **semana actual**
2. Usá los tabs **← Pasada / Esta semana / Próxima →** para navegar entre semanas
3. Cada día tiene 4 slots (Desayuno ☀️ / Almuerzo 🍽️ / Merienda ☕ / Cena 🌙)
4. Tocá el botón **＋** en cualquier slot para asignar un plato
5. En el buscador del modal, escribí el nombre de la receta o elegila de la lista
6. Si aún no tenés la receta cargada, tocá **"+ Crear plato nuevo"**
7. Una vez asignado, podés:
   - **⭕** marcar el plato como cocinado (queda con opacidad reducida)
   - **📖** ver la receta completa
   - **✕** quitar el plato del slot
8. Usá **📋 Copiar semana** para pasar todo el menú actual a la semana siguiente
9. Usá **🗑 Limpiar** para vaciar todos los slots de la semana actual

---

### Inventario

1. Entrá a la sección **Inventario** desde la barra de navegación
2. Ya encontrás **38 productos precargados** en 0 — todos los ingredientes comunes de cocina
3. Para actualizar stock, usá los botones **−** y **+** de cada producto
4. Para ajustar **unidad o fracción**, tocá el lápiz ✏️ y modificá los detalles:
   - Elegí entre u / kg / L / g / ml
   - Si usás kg, L o unidades, podés indicar fracción adicional (¼, ½, ¾)
5. Para agregar un **producto propio** (que no está en la lista), tocá **+ Agregar**:
   - Ingresá el nombre, elegí categoría, cantidad y unidad
   - Quedará disponible también al crear recetas
6. Los productos propios pueden eliminarse con 🗑; los precargados no se eliminan
7. Usá los **filtros de categoría** para ver solo un tipo de producto
8. El buscador superior filtra en tiempo real

#### Sobre las fracciones
La fracción representa la **porción adicional** que tenés disponible además de la cantidad entera. Por ejemplo:
- `2 kg + ½` significa que tenés 2 kg completos y además medio paquete más
- Al calcular la lista de compras, la fracción **se suma** como stock disponible
- Si la cantidad entera llega a 0, la fracción también se resetea automáticamente

---

### Recetas

1. Entrá a **Recetas** y tocá **+ Nueva receta**
2. Completá el **nombre del plato**
3. En el buscador de ingredientes, escribí el nombre y hacé clic en el que querés agregar
   - Si no existe, aparece la opción **"Agregar [nombre]"** que lo incorpora a la lista maestra
4. Para cada ingrediente seleccionado, configurá:
   - **Cantidad** (número)
   - **Unidad** (u / kg / g / L / ml)
   - **Fracción** (— / ¼ / ½ / ¾) — para cantidades como "1 kg ½"
5. Opcionalmente, escribí los **pasos de preparación** (uno por línea, con o sin numeración)
6. Tocá **Guardar receta**
7. Desde la lista de recetas podés:
   - Tocar una receta para **verla completa**
   - ✏️ **Editar** nombre, ingredientes o pasos
   - 🗑 **Eliminar** la receta

---

### Lista de compras

1. Planificá tu semana en el planificador con recetas asignadas
2. Asegurate de tener el inventario actualizado con lo que ya tenés en casa
3. Entrá a **Compras** y tocá **🔄 Regenerar**
4. La app calcula automáticamente qué ingredientes faltan y en qué cantidad
5. Marcá cada ítem con el checkbox a medida que comprás
6. Usá **+ Manual** para agregar productos que no vienen de recetas
7. Al terminar, tocá **📤 Exportar** para descargar la lista como `.txt`

---

### Opciones

| Opción | Descripción |
|---|---|
| Modo oscuro | Cambia el tema visual a tonos oscuros y cálidos |
| Tamaño de texto | Normal (16px) / Grande (19px) / Muy grande (22px) |
| Exportar datos | Descarga un `.json` con todo el contenido de la app |
| Importar datos | Restaura desde un `.json` exportado anteriormente |
| Borrar todo | Elimina todos los datos del dispositivo (irreversible) |

---

## Datos y almacenamiento

Todos los datos se guardan en el `localStorage` del navegador, bajo estas claves:

| Clave | Contenido |
|---|---|
| `mm_planner` | Menú semanal (slots asignados por semana/día/comida) |
| `mm_inventory` | Inventario de productos con cantidad y unidad |
| `mm_recipes` | Recetas con ingredientes y pasos |
| `mm_shopping` | Lista de compras actual |
| `mm_ingredients` | Lista maestra de ingredientes conocidos |
| `mm_settings` | Preferencias del usuario (tema, tamaño de fuente) |

**Importante:**
- Los datos son **locales al dispositivo y al navegador**. Si usás la app en Chrome y luego en Firefox, los datos no se comparten.
- Si borrás la caché del navegador o usás modo incógnito, los datos se pierden.
- **Recomendación**: exportá un backup periódico desde Opciones → Exportar datos.

---

## Instalación como app (PWA)

MiMenú puede instalarse como aplicación nativa en el celular sin pasar por ninguna tienda:

**En Android (Chrome):**
1. Abrí la app en Chrome
2. Tocá el menú (⋮) → **"Agregar a pantalla de inicio"**
3. Confirmá con **Instalar**

**En iOS (Safari):**
1. Abrí la app en Safari
2. Tocá el botón de compartir (□↑)
3. Seleccioná **"Agregar a pantalla de inicio"**
4. Tocá **Agregar**

Una vez instalada, la app abre en pantalla completa sin barra de navegador.

---

## Despliegue en GitHub Pages

El proyecto está pensado para publicarse fácilmente en GitHub Pages:

```bash
# 1. Crear un repositorio en GitHub (ej: mimenu)

# 2. Clonar el repositorio localmente
git clone https://github.com/tu-usuario/mimenu.git
cd mimenu

# 3. Copiar los archivos del proyecto
cp index.html manifest.json sw.js icon-192.png icon-512.png ./

# 4. Subir a GitHub
git add .
git commit -m "Primer deploy de MiMenú"
git push origin main

# 5. En GitHub → Settings → Pages → Source: main branch → /root
# La app quedará disponible en: https://tu-usuario.github.io/mimenu
```

---

## Paleta de colores

La paleta está inspirada en ingredientes y tonos de cocina.

### Modo claro

| Nombre | Hex | Uso |
|---|---|---|
| Crema cálida | `#FFF8F0` | Fondo principal |
| Durazno suave | `#FDEBD0` | Fondo secundario / cards |
| Naranja especiado | `#E07A3F` | Acento primario / botones |
| Verde albahaca | `#4A9E6B` | Acento secundario / confirmaciones |
| Rojo tomate | `#C0392B` | Alertas / eliminar |
| Marrón cacao | `#3D2B1F` | Texto principal |

### Modo oscuro

| Nombre | Hex | Uso |
|---|---|---|
| Carbón cálido | `#1C1410` | Fondo principal |
| Marrón oscuro | `#2C201A` | Fondo secundario / cards |
| Naranja llama | `#F0954A` | Acento primario / botones |
| Verde menta | `#62C28A` | Acento secundario / confirmaciones |
| Rojo pimentón | `#E05C4E` | Alertas / eliminar |
| Crema tostada | `#F5EAD8` | Texto principal |

---

## Roadmap

Funcionalidades planeadas para versiones futuras:

- [ ] **Perfil familiar / multiusuario** — organizar el menú considerando preferencias de cada integrante
- [ ] **Porcionado automático** — ajustar cantidades de ingredientes según número de comensales
- [ ] **Migración a React** — refactorización del frontend para mejor mantenibilidad
- [ ] **Backend opcional** — sincronización entre dispositivos para usuarios que lo necesiten
- [ ] **Etiquetas en recetas** — vegetariano, sin gluten, rápido, etc.
- [ ] **Historial de menús** — ver qué se cocinó en semanas anteriores
- [ ] **Notificaciones** — recordatorio diario del menú del día
- [ ] **Modo impresión** — vista optimizada del menú semanal para imprimir

---

## Licencia

Este proyecto es de uso personal y libre. Podés modificarlo y distribuirlo libremente.

---

*Desarrollado con HTML, CSS y JavaScript puro. Sin dependencias externas.*