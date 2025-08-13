# Simulador de Inscripción de Horarios

Un simulador web interactivo y avanzado para planificar y visualizar horarios académicos con funcionalidades inteligentes. Diseñado para ayudar a estudiantes y administradores a optimizar la selección de materias evitando conflictos de horarios, con sistema de reservas, selección manual inteligente y visualización interactiva.

[![Deployed on Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-black?style=flat&logo=vercel&logoColor=white)](https://simulador-inscripcion-horarios.krisv.dev/)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

![Simulador de Horarios](app.png)

## ¿Qué hace este proyecto?

El Simulador de Inscripción de Horarios es una herramienta avanzada que te permite:

- **Cargar datos de materias y horarios** desde un archivo JSON dinámicamente
- **Seleccionar materias y grupos** con tres modalidades distintas de selección
- **Generar combinaciones automáticamente** sin conflictos de horario con límites configurables
- **Visualizar horarios en un calendario semanal interactivo** con hover dinámico
- **Manejar grupos llenos** con sistema de reservas automáticas inteligente
- **Selección manual inteligente** con prevención automática de conflictos
- **Auto-llenado con reservas** para optimizar la selección automáticamente
- **Exportar selecciones** en formato JSON para uso posterior
- **Interfaz visual moderna** con tooltips informativos y calendario responsivo

## Características principales

### 🎯 Selección inteligente
- **Tres modalidades de selección**: Generación automática, auto-llenado con reservas y selección manual inteligente
- **Detección automática de conflictos** entre horarios en tiempo real
- **Prevención inteligente de empalmes** durante la selección manual con deshabilitación automática
- **Sistema de reservas avanzado** para manejar grupos llenos automáticamente
- **Auto-selección de materias** cuando se elige un grupo específico
- **Deshabilitación inteligente** de grupos conflictivos y de la misma materia
- **Gestión automática de grupos llenos** con prevención de selección
- **Límites configurables** de combinaciones para optimizar rendimiento

### 📅 Visualización interactiva
- **Calendario semanal visual** responsivo (Lunes a Viernes, 7:00-22:00)
- **Códigos de color únicos** generados automáticamente por materia usando algoritmo hash
- **Tooltips dinámicos avanzados** con hover que muestran grupos disponibles por horario específico
- **Información detallada en tiempo real** de profesores, grupos y disponibilidad
- **Indicadores visuales de estado** (disponible, lleno, seleccionado, misma materia)
- **Detección de hover por slots de tiempo** con precisión de 30 minutos
- **Posicionamiento inteligente de tooltips** que se ajustan a los bordes de pantalla
- **Actualización en tiempo real** del calendario con cada selección individual

### ⚡ Funciones avanzadas interactivas
- **Selección manual inteligente** que deshabilita automáticamente grupos conflictivos en tiempo real
- **Auto-llenado con reservas** que optimiza la selección evitando conflictos cuando es posible
- **Sistema inteligente de grupos llenos** con simulación realista de indisponibilidad
- **Prevención automática de conflictos** durante la selección individual de grupos
- **Reglas de negocio automáticas** (un grupo por materia, no grupos llenos, auto-selección de materias)
- **Gestión bidireccional de selecciones** (seleccionar grupo auto-selecciona materia, deseleccionar grupo puede deseleccionar materia)
- **Recalculación dinámica de conflictos** después de cada cambio de selección
- **Sistema de estados visuales** con clases CSS dinámicas para grupos deshabilitados
- **Exportación completa en JSON** de configuraciones para reutilización y backup
- **Carga dinámica asíncrona** de datos desde archivos JSON externos
- **Interfaz completamente responsive** con diseño moderno, accesible y optimizado
- **Sistema de tooltips avanzado** con información contextual y posicionamiento inteligente
- **Algoritmo de backtracking optimizado** para generación eficiente de miles de combinaciones
- **Hover dinámico con detección por slots** que muestra información precisa de cada franja horaria

## Estructura del proyecto

```
horarios/
├── index.html                              # Aplicación principal interactiva
├── horarios.json                           # Datos de materias y horarios
├── app.png                                 # Captura de pantalla de la aplicación
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
2. Abre `index.html` en tu navegador
3. La aplicación cargará automáticamente los datos y estará lista para usar

### 2. Selección de materias y grupos
- **Marca las materias** que quieras inscribir usando los checkboxes principales
- Cada materia muestra cuántos grupos tiene disponibles
- **Marca grupos específicos** usando los checkboxes individuales para selección manual
- **Marca grupos como "llenos"** para simular indisponibilidad y forzar alternativas

### 3. Modalidades de selección (¡3 formas diferentes!)

#### Modalidad A: Generación automática de combinaciones
1. Marca las materias deseadas (sin seleccionar grupos específicos)
2. Haz clic en **"Calcular combinaciones"**
3. El sistema generará automáticamente todas las combinaciones posibles sin conflictos
4. Navega por la lista de combinaciones y selecciona la que prefieras
5. Visualiza la combinación seleccionada en el calendario interactivo

#### Modalidad B: Auto-llenado inteligente con reservas
1. Marca las materias deseadas
2. Haz clic en **"Auto llenar (con reservas)"**
3. El algoritmo inteligente seleccionará automáticamente los primeros grupos disponibles sin conflictos
4. Si encuentra conflictos inevitables, agregará grupos adicionales como "reservas"
5. Ideal para obtener una selección rápida y optimizada

#### Modalidad C: Selección manual inteligente
1. **No uses los botones automáticos** - selecciona grupos individualmente
2. Marca directamente los checkboxes de los grupos específicos que deseas
3. **El sistema es inteligente**: automáticamente deshabilita grupos conflictivos en tiempo real
4. **Auto-selección de materias**: al seleccionar un grupo, la materia se marca automáticamente
5. **Solo un grupo por materia**: regla aplicada automáticamente con deshabilitación visual
6. **Prevención de grupos llenos**: los grupos marcados como "llenos" no pueden seleccionarse
7. **Recalculación dinámica**: después de cada selección/deselección se recalculan conflictos
8. **Gestión bidireccional**: deseleccionar el último grupo de una materia desmarca la materia
9. **Visualización en tiempo real**: el calendario se actualiza instantáneamente con cada cambio
10. Perfecto para cuando sabes exactamente qué grupos quieres con máxima flexibilidad

### 4. Visualización interactiva y exploración avanzada
- **Calendario semanal dinámico** con tu selección actual en colores únicos por materia
- **Hover avanzado por slots de tiempo** para ver tooltips informativos detallados con:
  - Grupos disponibles en cada franja horaria específica (precisión de 30 minutos)
  - Estado detallado de cada grupo (disponible, lleno, seleccionado, misma materia ya seleccionada)
  - Información completa de profesores y horarios específicos
  - Detección inteligente de overlapping entre horarios
- **Indicadores visuales de estado** en tiempo real con códigos de color
- **Posicionamiento inteligente de tooltips** que se ajustan a los bordes de pantalla
- **Actualización instantánea** del calendario con cada selección individual

### 5. Exportación y gestión
- **"Exportar selección (JSON)"** para guardar tu configuración completa
- **"Limpiar selección manual"** para resetear toda la selección manual
- **Toggle de límite de combinaciones** (recomendado: 2000 para mejor rendimiento)

## Configuración avanzada y características técnicas

### Límite de combinaciones inteligente
- **Por defecto**: 2000 combinaciones para rendimiento óptimo
- **Configurable**: Puedes desactivar el límite para explorar hasta 50,000 combinaciones
- **Recomendación**: Mantener activado para mejor experiencia de usuario
- **Algoritmo**: Utiliza backtracking optimizado para generar combinaciones eficientemente

### Sistema avanzado de grupos llenos
Marca cualquier grupo como "lleno" para:
- **Excluir automáticamente** de todas las generaciones automáticas
- **Simular escenarios reales** de inscripción universitaria
- **Forzar el sistema de reservas** para probar alternativas
- **Prevenir selección manual** de grupos no disponibles
- **No afecta otros grupos** - solo el específicamente marcado

### Funcionalidades interactivas del calendario
- **Hover dinámico por slots**: Muestra información detallada de grupos por franja horaria específica (30 min)
- **Tooltips informativos avanzados**: Incluyen estado detallado, profesor, horarios específicos y contexto de disponibilidad
- **Detección de overlapping**: Identifica automáticamente grupos que se superponen en tiempo
- **Estados visuales diferenciados**: Disponible (verde), lleno (rojo), seleccionado (azul), misma materia (amarillo)
- **Colores automáticos**: Generación de colores únicos por materia usando algoritmo hash determinista
- **Posicionamiento inteligente**: Tooltips que se ajustan automáticamente a los bordes de pantalla
- **Responsive design**: Adaptable a diferentes tamaños de pantalla con grid responsivo
- **Visualización en tiempo real**: Actualización instantánea con cada selección individual
- **Z-index optimizado**: Capas apropiadas para hover y visualización de clases

## Casos de uso típicos

### Para estudiantes:
- **Planificación semestral inteligente**: Diseña tu horario ideal con tres modalidades diferentes
- **Selección manual asistida**: Elige grupos específicos con prevención automática de conflictos
- **Visualización interactiva**: Ve tu carga académica semanal con tooltips informativos por horario
- **Gestión inteligente de backup**: Sistema automático de reservas para grupos llenos
- **Selección precisa con profesores**: Elige grupos específicos con información detallada de profesores
- **Simulación realista avanzada**: Prueba diferentes escenarios con grupos marcados como llenos
- **Feedback en tiempo real**: Obtén información instantánea sobre disponibilidad y conflictos
- **Exploración por horarios**: Descubre qué grupos están disponibles en cada franja horaria específica

### Para administradores académicos:
- **Análisis de conflictos**: Identifica empalmes en la programación institucional
- **Optimización de recursos**: Distribuye grupos para maximizar inscripciones
- **Planificación estratégica**: Evalúa capacidades y demanda por horarios
- **Simulación institucional**: Modela diferentes escenarios de oferta académica

## Nuevas características implementadas

### 🔄 Sistema de selección bidireccional inteligente
- **Auto-selección de materias**: Al seleccionar cualquier grupo, la materia correspondiente se marca automáticamente
- **Deselección inteligente**: Al deseleccionar el último grupo de una materia, la materia se desmarca automáticamente
- **Sincronización en tiempo real**: Cambios instantáneos entre grupos y materias para mantener consistencia

### 🚫 Sistema avanzado de deshabilitación de grupos
- **Deshabilitación por conflicto**: Grupos con horarios superpuestos se deshabilitan automáticamente
- **Deshabilitación por materia**: Solo un grupo por materia puede seleccionarse simultáneamente
- **Indicadores visuales**: Grupos deshabilitados muestran estados visuales diferenciados (opacidad, color)
- **Recalculación dinámica**: Después de cada cambio se recalculan automáticamente todos los conflictos

### 🎯 Tooltips avanzados por slots de tiempo
- **Detección por franja horaria**: Hover preciso en slots de 30 minutos dentro del calendario
- **Información contextual**: Muestra todos los grupos disponibles para ese horario específico
- **Estados diferenciados**: Disponible (verde), lleno (rojo), seleccionado (azul), misma materia (amarillo)
- **Posicionamiento inteligente**: Tooltips que se ajustan automáticamente a los bordes de pantalla
- **Información detallada**: Incluye profesor, grupo, horario exacto y estado de disponibilidad

### ⚡ Gestión de estado en tiempo real
- **Actualización instantánea del calendario**: Cada selección individual actualiza inmediatamente la visualización
- **Prevención de conflictos en vivo**: Sistema que previene selecciones conflictivas antes de que ocurran
- **Manejo de grupos llenos**: Prevención automática de selección de grupos marcados como no disponibles
- **Estados CSS dinámicos**: Aplicación automática de clases CSS para estados visuales

### 🔧 Mejoras técnicas de arquitectura
- **Event delegation optimizado**: Manejo eficiente de eventos para múltiples elementos
- **Algoritmo de overlap mejorado**: Detección precisa de conflictos de horario con precisión de minutos
- **Z-index management**: Gestión apropiada de capas para tooltips, hover y elementos del calendario
- **Responsive hover zones**: Áreas de hover optimizadas para diferentes tamaños de pantalla

### 🎨 Mejoras de experiencia de usuario (UX/UI)
- **Feedback visual instantáneo**: Estados visuales que cambian en tiempo real al seleccionar/deseleccionar
- **Indicadores de estado diferenciados**: Colores y estilos únicos para cada tipo de estado (disponible, lleno, seleccionado, conflictivo)
- **Deshabilitación visual clara**: Grupos no seleccionables muestran opacidad reducida y cursor bloqueado
- **Hover interactivo mejorado**: Efectos de hover sutiles que indican interactividad
- **Tooltips contextuales**: Información relevante que aparece exactamente donde el usuario la necesita
- **Transiciones suaves**: Animaciones CSS que mejoran la percepción de respuesta del sistema
- **Mensajes de error informativos**: Alertas claras que explican por qué una acción no es posible
- **Navegación intuitiva**: Flujo de trabajo que guía al usuario naturalmente a través de las opciones

## Resolución de problemas

### "Error al cargar horarios.json"
- **Ubicación**: Verifica que el archivo esté en la misma carpeta que `index.html`
- **Formato**: Asegúrate de que el JSON tenga la estructura correcta
- **Permisos**: Ejecuta desde un servidor web local si es necesario
- **Debugging**: Revisa la consola del navegador (F12) para detalles específicos

### "No hay combinaciones sin empalmes"
- **Reducir materias**: Disminuye el número de materias seleccionadas simultáneamente
- **Gestión de grupos llenos**: Desmarca algunos grupos marcados como "llenos"
- **Verificar disponibilidad**: Asegúrate de que haya al menos un grupo disponible por materia
- **Usar reservas**: Prueba el auto-llenado con reservas para soluciones alternativas

### Rendimiento lento o navegador no responde
- **Límite activado**: Mantén el límite de 2000 combinaciones habilitado
- **Selección gradual**: Reduce materias y aumenta progresivamente
- **Usar auto-llenado**: Considera usar la función automática en lugar de generar todas las combinaciones
- **Navegador actualizado**: Usa versiones recientes de Chrome, Firefox o Safari

### Problemas de visualización
- **Zoom del navegador**: Asegúrate de que esté al 100%
- **Resolución**: Funciona mejor en pantallas de al menos 1024px de ancho
- **JavaScript habilitado**: Verifica que esté activado en la configuración del navegador

## Personalización y adaptación

Para adaptar el simulador a tu institución específica:

### Datos académicos
1. **Actualiza `horarios.json`** con tus materias, grupos y profesores específicos
2. **Mantén la estructura JSON** definida para compatibilidad completa
3. **Incluye todos los horarios** de cada grupo para detección correcta de conflictos

### Configuración de horarios
- **Rango de horas**: Modifica las constantes de tiempo en el código (líneas 667-668)
  - Por defecto: 7:00 AM a 10:00 PM
  - Intervalos: 30 minutos por slot
- **Días de la semana**: Actualmente soporta Lunes a Viernes (LU-VI)

### Personalización visual
- **Colores**: El sistema genera automáticamente colores únicos por materia
- **Estilos**: Personaliza el CSS en la sección `<style>` del archivo `index.html`
- **Responsive**: El diseño se adapta automáticamente a diferentes pantallas
- **Tema**: Fácil modificación de variables CSS para cambiar la apariencia completa

## Tecnologías utilizadas

### Core Technologies
- **HTML5** para la estructura semántica y moderna
- **CSS3** con Flexbox y Grid para diseño responsive avanzado
- **JavaScript ES6+** vanilla para toda la lógica, sin dependencias externas
- **JSON** para almacenamiento y estructura de datos

### Características técnicas avanzadas
- **Algoritmos de backtracking optimizado** para generación eficiente de combinaciones
- **Detección de conflictos en tiempo real** con análisis de overlapping por día y horario
- **Sistema de eventos dinámicos** para interactividad responsive con event delegation
- **Hover tooltips avanzados** con posicionamiento inteligente y detección por slots de tiempo
- **Hash-based color generation** para colores únicos automáticos y deterministas
- **Gestión de estado bidireccional** entre grupos y materias con sincronización automática
- **Recalculación dinámica de conflictos** después de cada cambio con optimización de rendimiento
- **Sistema de clases CSS dinámicas** para estados visuales de grupos (enabled/disabled)
- **Detección precisa de overlapping** con precisión de minutos para validación de conflictos
- **Event listeners optimizados** para selección de grupos con prevención de conflictos en tiempo real
- **Responsive design** con media queries, grid layout y elementos adaptivos
- **Z-index management** para capas de hover, tooltips y elementos del calendario

### Arquitectura del proyecto
- **Single-page application** completamente funcional
- **Separación de concerns** entre lógica, presentación y datos
- **Event-driven programming** para máxima interactividad
- **Performance optimizado** con límites configurables y rendering eficiente

## Reglas de negocio implementadas

### 🔒 Reglas automáticas estrictas
1. **Un grupo por materia**: Solo se puede seleccionar un grupo por materia simultáneamente
2. **No grupos llenos**: Los grupos marcados como "llenos" no pueden seleccionarse
3. **No conflictos de horario**: Grupos con horarios superpuestos se deshabilitan automáticamente
4. **Auto-selección de materias**: Seleccionar un grupo automáticamente marca la materia correspondiente
5. **Deselección inteligente**: Deseleccionar el último grupo de una materia desmarca la materia

### 🔄 Reglas de recalculación dinámica
- **Recalculación después de cada cambio**: Todos los conflictos se recalculan automáticamente
- **Habilitación/deshabilitación en tiempo real**: Estados visuales se actualizan instantáneamente
- **Prevención proactiva**: El sistema previene conflictos antes de que ocurran
- **Consistencia de estado**: Sincronización automática entre grupos, materias y calendario

## Contribuciones y mejoras futuras

Este proyecto está diseñado para ser fácilmente extensible. Ideas implementables:

### Funcionalidades próximas
- **Soporte para horarios de fin de semana** (sábados/domingos)
- **Integración con APIs** y bases de datos institucionales
- **Exportación multi-formato** (PDF, Excel, iCal)
- **Sistema de notificaciones** para cambios de horario en tiempo real
- **Modo oscuro** con toggle automático
- **Historial de selecciones** con sistema de deshacer/rehacer
- **Comparador de combinaciones** lado a lado

### Mejoras técnicas
- **Progressive Web App (PWA)** para uso offline
- **Drag & drop** para reordenamiento visual en el calendario
- **Filtros avanzados** por profesor, horario, modalidad, disponibilidad
- **Algoritmos de optimización** para encontrar las mejores combinaciones
- **Cache inteligente** para datos de horarios frecuentemente utilizados
- **Validación de datos** más robusta para archivos JSON
- **Sistema de plugins** para extensiones personalizadas

---

**Desarrollado por Kristoffer Van ([@im-krizox](https://github.com/im-krizox))**

*Proyecto diseñado para facilitar la planificación académica y optimizar la experiencia de inscripción de horarios universitarios. Open source bajo licencia MIT.*
