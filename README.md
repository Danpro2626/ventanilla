<div align="center">

# 🎫 Ventanilla

### Todos tus trámites universitarios en un solo lugar.
**Sin filas. Sin ir 3 veces.**

<br>

![HTML5](https://img.shields.io/badge/HTML5-14213D?style=for-the-badge&logo=html5&logoColor=FFC53D)
![CSS3](https://img.shields.io/badge/CSS3-14213D?style=for-the-badge&logo=css3&logoColor=FFC53D)
![JavaScript](https://img.shields.io/badge/JavaScript-14213D?style=for-the-badge&logo=javascript&logoColor=FFC53D)
![Sin dependencias](https://img.shields.io/badge/dependencias-0-0F766E?style=for-the-badge)
![Universidades](https://img.shields.io/badge/universidades-133-FFC53D?style=for-the-badge&labelColor=14213D)

<br>

[Ver demo](#-probarlo-en-30-segundos) · [Funciones](#-qué-puedes-hacer) · [Personalizar](#-personalízalo) · [Roadmap](#-roadmap)

</div>

---

## 👋 ¿Qué es Ventanilla?

Pedir un certificado, homologar materias o reservar una cita de bienestar suele significar buscar en cinco páginas distintas y aun así llegar a la oficina sin un documento.

**Ventanilla** junta todo en una sola app: eliges tu universidad, le preguntas al asistente con tus propias palabras y te dice **qué llevar, cuánto cuesta y dónde hacerlo**. Después sigues tu trámite paso a paso y reservas tu cita sin hacer fila.

> Es una app de una sola página, hecha con HTML, CSS y JavaScript puros. Sin frameworks, sin servidor y sin instalar nada.

---

## ✨ Qué puedes hacer

### 🔎 Encuentra tu universidad
Un buscador con **133 universidades e instituciones** de Colombia.

- Búsqueda en vivo que ignora tildes y mayúsculas, con la coincidencia resaltada.
- Filtros **Todas / Públicas / Privadas** con contador de resultados.
- Resultados agrupados: *Bogotá · Públicas*, *Bogotá · Privadas* y *Otras ciudades*.
- Navegación completa con teclado: <kbd>↑</kbd> <kbd>↓</kbd> para moverte, <kbd>Enter</kbd> para elegir y <kbd>Esc</kbd> para cerrar.
- Recuerda tu elección la próxima vez que entres.
- Botón directo al sitio oficial de tu universidad.

### 💬 Asistente de trámites
Pregunta como hablas: *"¿qué necesito para un certificado de notas?"*

| Trámite | Qué te explica |
|---|---|
| Certificado de notas | Requisitos, costo y oficina |
| Certificado de estudio | Requisitos, costo y oficina |
| Homologación o transferencia | Documentos y a quién pedirla |
| Paz y salvo | Qué debes estar al día |
| Cancelación de materias | Plazos y aprobaciones |
| Cita con Bienestar | Cómo reservarla |

Cada respuesta trae una **lista de requisitos que puedes ir marcando**. El contador te avisa cuántos documentos te faltan, y cuando los tienes todos te dice que ya puedes hacer el trámite.

### 📋 Mis trámites
Sigue cada solicitud con una línea de progreso: **Solicitado → En revisión → Listo para recoger**. Puedes iniciar un trámite desde el asistente o desde la pestaña, y simular el avance para demostraciones.

### 🧠 Citas de bienestar
Elige el día (solo hábiles), la hora y el servicio: psicología, orientación académica, trabajo social o salud y enfermería. Incluye la opción de **reservar de forma discreta**, que oculta el servicio en tu lista.

---

## 🚀 Probarlo en 30 segundos

No hay nada que instalar.

```bash
# 1. Clona el repositorio
git clone https://github.com/TU-USUARIO/ventanilla.git

# 2. Entra a la carpeta
cd ventanilla

# 3. Abre el archivo en tu navegador
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

También puedes hacer doble clic en `index.html`, o publicarlo gratis con **GitHub Pages**:

1. Ve a **Settings → Pages**.
2. En *Source* elige la rama `main` y la carpeta `/ (root)`.
3. Guarda. En un par de minutos tendrás tu enlace público.

---

## 🛠️ Personalízalo

Todo vive en un solo archivo, así que ajustar los datos es sencillo.

### Agregar una universidad

Busca el arreglo `UNIS` dentro del `<script>` y añade una línea:

```js
{
  id: "mi-universidad",
  n: "Mi Universidad",
  c: "Bogotá",                  // ciudad o ciudades
  t: "Privada",                 // "Pública" o "Privada"
  web: "https://miuniversidad.edu.co",
  reg: "Registro Académico"     // oficina que atiende los trámites
}
```

### Agregar costos verificados

Añade `costos` a la universidad. Si `ok` es `true`, se muestra la etiqueta **Verificado**.

```js
costos: {
  "cert-notas": { v: "$12.000 pregrado activo", ok: true }
}
```

### Agregar un trámite nuevo

En el arreglo `KB` define las palabras clave que activan la respuesta y los requisitos:

```js
{
  id: "carne",
  nombre: "Duplicado del carné",
  keys: ["carne", "carnet", "duplicado"],
  req: ["Documento de identidad", "Recibo de pago"],
  donde: "{reg}"                // se reemplaza por la oficina de cada universidad
}
```

### Cambiar los colores

Los colores están en variables CSS al inicio del archivo:

```css
:root{
  --ink:#14213D;      /* azul marino */
  --ticket:#FFC53D;   /* amarillo turno */
  --teal:#0F766E;     /* verde agua */
}
```

---

## 🎨 Diseño

La interfaz está pensada como una **ventanilla de atención**: el turno amarillo con número, el azul marino de la oficina y bordes con sombra dura, como un sello.

- **Tipografías:** [Bricolage Grotesque](https://fonts.google.com/specimen/Bricolage+Grotesque) para títulos y [Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3) para el texto.
- **Responsive:** funciona en celular, tableta y computador.
- **Accesible:** foco visible con teclado, roles ARIA en el buscador y las pestañas, y respeto por la opción de reducir animaciones.

---

## 📁 Estructura

```
ventanilla/
├── index.html    # La app completa: estructura, estilos y lógica
└── README.md
```

---

## ⚠️ Importante

- **Es una demostración.** Los trámites y las citas se guardan solo en tu navegador (`localStorage`); no se envía nada a ninguna universidad.
- **Los costos y requisitos son orientativos.** La mayoría aparece como *Sin verificar*. Confirma siempre los valores vigentes en el sitio oficial de tu universidad.
- Las horas de las citas son de ejemplo.

---

## 🗺️ Roadmap

- [ ] Conectar con los portales reales de cada universidad
- [ ] Costos y requisitos verificados para más instituciones
- [ ] Notificaciones y recordatorios de citas
- [ ] Modo oscuro completo
- [ ] Más trámites: grados, reintegros y becas

---

## 🤝 Contribuir

¿Conoces los requisitos reales de tu universidad? Es la ayuda más valiosa.

1. Haz un **fork** del proyecto.
2. Crea una rama: `git checkout -b mejora/mi-universidad`
3. Haz tus cambios y un commit: `git commit -m "Agrega requisitos de Mi Universidad"`
4. Sube la rama y abre un **Pull Request**.

---

## 📄 Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE` para más información.

<div align="center">

<br>

Hecho con 💛 para que nadie vuelva a hacer fila por un certificado.

</div>
