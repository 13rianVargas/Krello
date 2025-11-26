# 📋 Krello

**Krello** es una aplicación de gestión de proyectos inspirada en Trello, desarrollada como proyecto final de la materia **Técnicas de Programación II** en la **Universidad Konrad Lorenz**.

---

## 📖 Descripción

Krello es un sistema de gestión de tareas basado en tableros Kanban que permite a los usuarios organizar proyectos de manera visual y colaborativa. La aplicación implementa el patrón de arquitectura **MVC (Modelo-Vista-Controlador)** y está desarrollada completamente en **Java** utilizando **Swing** para la interfaz gráfica.

---

## ✨ Características

### Gestión de Usuarios
- 👤 Registro e inicio de sesión de usuarios
- 🔐 Autenticación con correo electrónico y contraseña
- 👑 Roles diferenciados: **Administrador** y **Colaborador**

### Gestión de Tableros
- 📌 Crear, editar y eliminar tableros
- 👥 Invitar colaboradores a los tableros
- 🏷️ Asignar nombres personalizados a cada tablero

### Gestión de Listas
- 📝 Crear múltiples listas dentro de cada tablero
- ✏️ Editar y eliminar listas existentes
- 📂 Organización tipo Kanban (Por hacer, En progreso, Completado, etc.)

### Gestión de Tareas
- ✅ Crear tareas con descripción y fecha de vencimiento
- 👷 Asignar delegados/colaboradores a las tareas
- ☑️ Marcar tareas como completadas
- ⏰ Validación de horario laboral (8:00 AM - 5:00 PM)

### Funcionalidades Adicionales
- 🎨 Interfaz gráfica intuitiva con diseño Nimbus Look and Feel
- ⚡ Validación visual con efectos de parpadeo en campos incorrectos
- 📊 Control de disponibilidad de colaboradores (máximo 5 tareas por colaborador)

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Uso |
|------------|-----|
| **Java** | Lenguaje de programación principal |
| **Java Swing** | Interfaz gráfica de usuario (GUI) |
| **MVC** | Patrón de arquitectura |
| **Java Time API** | Manejo de fechas y horarios |

---

## 📁 Estructura del Proyecto

```
src/
├── module-info.java
└── co/
    └── edu/
        └── konradlorenz/
            ├── controller/
            │   ├── AplMain.java          # Punto de entrada de la aplicación
            │   └── Controlador.java      # Controlador principal (lógica de negocio)
            ├── model/
            │   ├── Persona.java          # Clase abstracta base para usuarios
            │   ├── Administrador.java    # Usuario con rol de administrador
            │   ├── Colaborador.java      # Usuario con rol de colaborador
            │   ├── Tablero.java          # Representación de un tablero Kanban
            │   ├── Lista.java            # Listas dentro de un tablero
            │   ├── Tarea.java            # Tareas dentro de una lista
            │   └── WorkTime.java         # Interfaz para validación de horario laboral
            └── view/
                ├── Vista.java            # Vista de consola (mensajes)
                └── gui/
                    ├── Login.java        # Ventana de inicio de sesión/registro
                    ├── Principal.java    # Ventana principal con tableros
                    └── FrameTablero.java # Ventana de tablero con listas y tareas
```

---

## 🚀 Instalación y Ejecución

### Requisitos Previos
- **Java JDK 11** o superior
- IDE compatible con Java (Eclipse, IntelliJ IDEA, NetBeans, VS Code)

### Pasos de Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/13rianVargas/Krello.git
   cd Krello
   ```

2. **Importar el proyecto en tu IDE**
   - En Eclipse: `File > Import > Existing Projects into Workspace`
   - En IntelliJ: `File > Open` y seleccionar la carpeta del proyecto

3. **Compilar y ejecutar**
   - Ejecutar la clase `AplMain.java` ubicada en `src/co/edu/konradlorenz/controller/`

### Compilación Manual (Terminal)
```bash
# Compilar
javac -d bin src/module-info.java src/co/edu/konradlorenz/**/*.java

# Ejecutar
java -p bin -m krello/co.edu.konradlorenz.controller.AplMain
```

---

## 📝 Uso

### Credenciales de Prueba

| Correo | Contraseña | Rol |
|--------|------------|-----|
| `admin` | `admin` | Administrador |
| `alejaqt@gmail.com` | `123` | Administrador |
| `sharina@gmail.com` | `123` | Administrador |
| `briscuit@gmail.com` | `123` | Administrador |
| `juan.perez@example.com` | `123` | Colaborador |

### Flujo de Uso

1. **Iniciar sesión** con las credenciales proporcionadas o **crear una cuenta nueva**
2. **Crear un tablero** desde la ventana principal
3. **Agregar listas** al tablero (ej: "Por Hacer", "En Progreso", "Completado")
4. **Crear tareas** dentro de las listas con fecha de vencimiento
5. **Invitar colaboradores** al tablero para trabajo en equipo
6. **Gestionar tareas** marcándolas como completadas

---

## 🏗️ Arquitectura MVC

```
┌─────────────────────────────────────────────────────────────┐
│                         VISTA (View)                        │
│  ┌─────────┐    ┌───────────┐    ┌──────────────────┐      │
│  │  Login  │    │ Principal │    │  FrameTablero    │      │
│  └────┬────┘    └─────┬─────┘    └────────┬─────────┘      │
│       │               │                    │                │
└───────┼───────────────┼────────────────────┼────────────────┘
        │               │                    │
        └───────────────┼────────────────────┘
                        ▼
┌─────────────────────────────────────────────────────────────┐
│                    CONTROLADOR (Controller)                 │
│               ┌──────────────────────────┐                  │
│               │      Controlador         │                  │
│               │  - Lógica de negocio     │                  │
│               │  - Validaciones          │                  │
│               │  - Acciones de usuario   │                  │
│               └────────────┬─────────────┘                  │
└────────────────────────────┼────────────────────────────────┘
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                       MODELO (Model)                        │
│  ┌─────────┐  ┌────────┐  ┌───────┐  ┌─────────────────┐   │
│  │ Persona │  │Tablero │  │ Lista │  │      Tarea      │   │
│  ├─────────┤  └────────┘  └───────┘  └─────────────────┘   │
│  │Admin    │                                                │
│  │Colabor  │                                                │
│  └─────────┘                                                │
└─────────────────────────────────────────────────────────────┘
```

---

## 👥 Autores

Este proyecto fue desarrollado por estudiantes de **Ingeniería de Sistemas** de la **Universidad Konrad Lorenz**:

| Nombre | GitHub |
|--------|--------|
| **Alexander Chacon** | - |
| **Sharon Cruz** | - |
| **Nicoll Durán** | - |
| **Brian Vargas** | [@13rianVargas](https://github.com/13rianVargas) |

---

## 📄 Licencia

Este proyecto fue creado con fines académicos como parte del curso de **Técnicas de Programación II**.

---

## 🙏 Agradecimientos

- **Universidad Konrad Lorenz** - Fundación Universitaria
- Profesores del curso de **Técnicas de Programación II**
- [Trello](https://trello.com/) - Por la inspiración del diseño y funcionalidad

---

<p align="center">
  <b>Hecho con ❤️ en Colombia 🇨🇴</b>
</p>
