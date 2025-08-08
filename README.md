# Simulador de Inscripción de Horarios

Un simulador web interactivo para planificar y visualizar horarios académicos, diseñado para ayudar a estudiantes y administradores a optimizar la selección de materias evitando conflictos de horarios.

## ¿Qué hace este proyecto?

El Simulador de Inscripción de Horarios es una herramienta que te permite:

- **Cargar datos de materias y horarios** desde un archivo JSON
- **Seleccionar materias deseadas** y ver todos los grupos disponibles
- **Generar combinaciones automáticamente** sin conflictos de horario
- **Visualizar horarios en un calendario semanal** intuitivo
- **Manejar grupos llenos** con sistema de reservas automáticas
- **Exportar selecciones** para uso posterior

## Características principales

### 🎯 Selección inteligente
- Detecta automáticamente conflictos entre horarios
- Genera todas las combinaciones posibles sin empalmes
- Sistema de reservas para manejar grupos llenos

### 📅 Visualización clara
- Calendario semanal visual (Lunes a Viernes, 7:00-22:00)
- Códigos de color únicos por materia
- Información detallada de cada clase

### ⚡ Funciones avanzadas
- Selección manual grupo por grupo con prevención de conflictos
- Auto-llenado inteligente con manejo de reservas
- Límite configurable de combinaciones para mejor rendimiento

## Estructura del proyecto

```
horarios/
├── simulador_de_inscripcion_horarios.html  # Aplicación principal
├── horarios.json                           # Datos de materias y horarios
└── README.md                              # Este archivo
```

## Estructura del archivo JSON

El archivo `horarios.json` contiene un array de objetos, donde cada objeto representa un grupo específico de una materia:

```json
[
  {
    "materia": "Nombre de la materia",
    "grupo": "Código del grupo (ej: 1701)",
    "horarios": [
      {
        "dia": "Día de la semana (LU/MA/MI/JU/VI)",
        "inicio": "Hora de inicio (HH:MM)",
        "fin": "Hora de fin (HH:MM)"
      }
    ],
    "profesor": "Nombre del profesor"
  }
]
```

### Ejemplo práctico:

```json
{
  "materia": "Sistemas operativos",
  "grupo": "1702",
  "horarios": [
    { "dia": "MA", "inicio": "09:00", "fin": "11:00" },
    { "dia": "JU", "inicio": "09:00", "fin": "11:00" }
  ],
  "profesor": "Loza Pacheco Dulce Lourdes"
}
```

### Códigos de días:
- `LU`: Lunes
- `MA`: Martes  
- `MI`: Miércoles
- `JU`: Jueves
- `VI`: Viernes

## Cómo usar el simulador

### 1. Preparación inicial
1. Asegúrate de tener el archivo `horarios.json` en la misma carpeta que el HTML
2. Abre `simulador_de_inscripcion_horarios.html` en tu navegador

### 2. Selección de materias
- **Marca las materias** que quieras inscribir usando los checkboxes
- Cada materia muestra cuántos grupos tiene disponibles
- Puedes marcar grupos como "llenos" para simular indisponibilidad

### 3. Métodos de selección

#### Opción A: Generación automática de combinaciones
1. Haz clic en **"Calcular combinaciones"**
2. El sistema generará todas las combinaciones posibles sin conflictos
3. Selecciona una combinación de la lista para visualizarla

#### Opción B: Auto-llenado inteligente
1. Haz clic en **"Auto llenar (con reservas)"**
2. El sistema seleccionará automáticamente grupos sin conflictos
3. Si hay conflictos inevitables, agregará grupos como "reservas"

#### Opción C: Selección manual
1. Marca individualmente los grupos que deseas
2. El sistema deshabilitará automáticamente grupos conflictivos
3. Solo puedes seleccionar un grupo por materia

### 4. Visualización y exportación
- El calendario muestra tu selección actual con colores únicos por materia
- Usa **"Exportar selección (JSON)"** para guardar tu configuración
- **"Limpiar selección manual"** para empezar de nuevo

## Configuración avanzada

### Límite de combinaciones
Por defecto, el sistema limita las combinaciones a 2000 para mantener un rendimiento óptimo. Puedes desactivar esta opción si necesitas explorar más posibilidades, aunque esto puede hacer más lenta la aplicación.

### Manejo de grupos llenos
Marca cualquier grupo como "lleno" para:
- Excluirlo de las combinaciones automáticas
- Simular escenarios reales de inscripción
- Probar el sistema de reservas

## Casos de uso típicos

### Para estudiantes:
- Planificar tu horario del semestre
- Encontrar la mejor combinación de materias
- Visualizar tu carga académica semanal
- Tener alternativas en caso de grupos llenos

### Para administradores académicos:
- Analizar conflictos en la programación de horarios
- Optimizar la distribución de grupos
- Planificar capacidades y recursos

## Resolución de problemas

### "Error al cargar horarios.json"
- Verifica que el archivo esté en la misma carpeta que el HTML
- Asegúrate de que el JSON tenga el formato correcto
- Revisa la consola del navegador para más detalles

### "No hay combinaciones sin empalmes"
- Reduce el número de materias seleccionadas
- Marca algunos grupos como llenos para forzar alternativas
- Verifica que haya grupos disponibles para todas las materias

### Rendimiento lento
- Activa el límite de 2000 combinaciones
- Reduce el número de materias seleccionadas simultáneamente
- Considera usar la función de auto-llenado

## Personalización

Para adaptar el simulador a tu institución:

1. **Modifica `horarios.json`** con tus datos específicos
2. **Ajusta los horarios** cambiando las constantes de tiempo en el código (línea 406)
3. **Personaliza los estilos** editando el CSS en la sección `<style>`

## Tecnologías utilizadas

- **HTML5** para la estructura
- **CSS3** para el diseño responsive
- **JavaScript vanilla** para toda la lógica
- **JSON** para el almacenamiento de datos

## Contribuciones

Este proyecto está diseñado para ser fácilmente extensible. Algunas ideas para mejoras:

- Soporte para horarios de fin de semana
- Integración con bases de datos
- Exportación a diferentes formatos (PDF, Excel)
- Sistema de notificaciones para cambios de horario
- Modo oscuro

---

*Desarrollado para facilitar la planificación académica y optimizar la experiencia de inscripción de horarios.*
