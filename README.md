# Auditoría cruzada — ViaUtec

> **Plantilla de ejemplo para la actividad presencial de UTEC.** 



## 1. Datos de la auditoría

| Campo | Información |
|---|---|
| Equipo auditor | [The CodeCrew] |
| Equipo auditado | [Classteam / ViaUtec] |
| Sistema | Plataforma de viajes |
| Fecha | [2026-10-14] |
| Ambiente autorizado | App |
| Versión / commit | [1.0] |
| Navegador y dispositivo | Dispositivo movil  |
| Alcance | login, permisos y validaciones |

## 2. Resumen ejecutivo

**Objetivo:** evaluar la usabilidad, las validaciones funcionales, la seguridad de acceso y la consistencia de las operaciones de pago en un ambiente de pruebas.

**Resultado general:** Probamos el Registro de usuarios, creacion de viajes y unirnos a un viaje.



| Severidad | Cantidad |
|---|---:|
| Crítica | [0] |
| Alta | [0] |
| Media | [2] |
| Baja | [1] |

## 3. Funcionalidades revisadas

- [X] Inicio de sesión y cierre de sesión.
- [X] Registro de usuarios.
- [X] Creacion de viajes.
- [X] Unirte a un viaje.

## 4. Hallazgos

### H-01 — Calculo de valor del viaje

- **Categoría:** UX / actualizacion de datos.
- **Severidad sugerida:** baja .
- **Descripción:** Al seleccionar un viaje muestra un monton, al cambiar origen no cambia el precio.
- **Precondiciones:** usuario de prueba autenticado y un viaje creado.
- **Pasos para reproducir:**
  1. Abrir un viaje.
  2. Seleccionar una localidad de origen.
  3. Confirmar el viaje.
  4. El viaje queda pendiente de aprobación
- **Resultado esperado:** El monto debe variar según los kilometros del viaje basados en el precio que carga el conductor del viaje.
- **Resultado obtenido:** El monto solo es dividido entre los integrantes del viaje ignorando la distancia.


### H-02 — Registro de administrativo

- **Categoría:** Funcionalidad / flujo de creacion.
- **Severidad:** Media.
- **Descripción:** en la creacion de un usuario administrativo, puede suceder que en la segunda pestaña no te permita continuar incluso al llenar los campos requeridos.
- **Pasos para reproducir:**
  1. Ir al registro.
  2. Llenar campos primera pestaña.
  3. Presionar el boton siguiente.
  4. Llenar campos segunda pestaña.
  5. Presionar el boton siguiente.
- **Resultado esperado:** Debe de pasar a una tercera pestaña de datos a completar.
- **Resultado obtenido:** En algunas oportunidades no se nos permitio precionar el boton.
- **Recomendación:** El error no se manifiesta siempre. Para solucionarlo debes de volver a la primera pestaña y cambiar el tipo de usuario y luego volver a seleccionar administrativo.

### H-03 — Creacion dos viajes mismo conductor.

- **Categoría:** Funcionalidad .
- **Severidad:** Media.
- **Descripción:** verificar que un usuario no pueda crear dos viajes distintos con misma fecha y hora con origenes y destinos diferentes.
- **Pasos para reproducir:** Agendamos un viaje con el mismo origen y destino como conductor previamente logueados luego agendamos otro viaje con la misma fecha y hora que el viaje anterior seleccionando mismo origen y mismo destino que el viaje anterior.
- **Resultado esperado:** No debe permitir agendar el segundo viaje tampoco debe permitir seleccionar un mismo origen y destino.
- **Resultado obtenido:** Permite la creacion del segundo viaje.

## 5. Matriz consolidada

| ID | Categoría | Hallazgo o prueba | Severidad | Estado |
|---|---|---|---|---|---|
| H-01 | UX | Calculo valos de viaje | Baja | Pendiente de revision | 
| H-02 | Funcionalidad | Registro administrativo | Media | Pendiente de verificar frecuencia|
| H-03 | Funcionalidad | Creacion de viajes del mismo conductor | Media | Prueba ejecutada | 



