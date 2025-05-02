# Actividad3T-BBDD
# 📚 Sistema de Gestión de Préstamos - Biblioteca Municipal

Este proyecto implementa un sistema de gestión de préstamos de libros en una biblioteca municipal utilizando una base de datos relacional. El sistema permite registrar usuarios, libros, gestionar préstamos y aplicar sanciones por retrasos en la devolución.

## 📦 Contenido de la Entrega

- `diagramas.pdf`: Documento con el Diagrama Entidad-Relación (ER) y el Diagrama Funcional, ambos acompañados de sus respectivas explicaciones.
- `biblioteca.sql`: Script SQL único que incluye:
  - Creación de las 4 tablas principales.
  - Procedimientos de inserción de datos para usuarios, libros y préstamos.
  - Funciones de sanción y generación de mensajes.
  - Procedimiento `GESTOR` para aplicar sanciones y registrar infracciones.

---

## 🗂️ Estructura de la Base de Datos

### Tablas Principales

1. **Usuarios**: Almacena la información básica de cada usuario.
2. **Libros**: Contiene los datos identificativos de cada libro (ISBN, título, autor, etc.).
3. **Prestamos**: Registra los préstamos realizados, con fechas de entrega y devolución, nivel de sanción y mensaje asociado.
4. **Sancionados**: Tabla adicional que registra los usuarios sancionados con nivel GRAVE o MUY GRAVE.

---

## ⚙️ Procedimientos

### `insertar_usuario`
Registra un nuevo usuario en la base de datos con los datos necesarios.

### `insertar_libro`
Da de alta un nuevo libro cuando este llega a la biblioteca.

### `insertar_prestamo`
Registra un nuevo préstamo asociado a un usuario y un libro.

---

## 🧠 Funciones

### `SANCION_USUARIO`
Calcula la gravedad de la sanción en base a los días de retraso:
- `ACTIVO`: ≤ 7 días.
- `GRAVE`: > 7 y < 12 días.
- `MUY GRAVE`: ≥ 12 días.

### `MENSAJE_SANCION`
Genera un mensaje personalizado para el usuario con los detalles del préstamo y la sanción aplicable.

---

## 🔄 Procedimiento `GESTOR`

Este procedimiento:
1. Recorre la tabla de préstamos.
2. Aplica las funciones `SANCION_USUARIO` y `MENSAJE_SANCION`.
3. Actualiza los campos `NIVEL_SANCION` y `MENSAJE`.
4. Inserta en la tabla `SANCIONADOS` a todos los usuarios con sanciones GRAVE o MUY GRAVE, incluyendo:
   - Código de usuario.
   - Fecha del préstamo.
   - Días de sanción.
   - Mensaje generado.

---

## 💾 Datos de Prueba

En el archivo `biblioteca.sql` se incluyen también:
- Ejecuciones de los procedimientos de inserción con datos de ejemplo.
- Casos de sanciones activadas para demostrar el correcto funcionamiento del sistema.

---

## 🧩 Requisitos Técnicos

- Motor de base de datos: **MySQL**
- Editor de SQL recomendado: **MySQL Workbench**

---

## 📑 Autor

Autor: Arantza Alcázar  

---
